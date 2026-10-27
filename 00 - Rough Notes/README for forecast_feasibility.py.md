## forecast_feasibility.py

Feasibility checks for the forecasting pivot. The question is whether a model trained on summer
MIMIC-III data can forecast seasonal ICU demand 7 days ahead, and whether KSWIN-triggered
retraining recovers the accuracy it loses in winter.

The script answers five questions, each with one figure:

| # | Question | Figure | `summary.md` section |
|---|---|---|---|
| 1 | Does each candidate series rise in winter by more than its day-to-day noise? | `fig1_composite_series.png` | 1 |
| 2 | Does the date shifting keep exact calendar days, or smear them? | `fig2_date_shift_checks.png` | 2 |
| 3 | Does a summer-trained forecaster get worse in winter, and does refitting recover it? | `fig3_degradation_proxy.png` | 3 |
| 4 | Does KSWIN fire near flu-season onset or offset at day-scale windows? | `fig4_kswin_alarms.png` | 4 |
| 5 | What drives the summer-to-winter rise in hospital mortality? | `fig5_mortality_decomposition.png` | 5 |

Part 1 explains how to run it and what every function does. Part 2 explains how to read every
output, including baselines, rough expected values and pitfalls.

---

## Running it

```bash
python forecast_feasibility.py --mimic-dir /path/to/mimic-iii-clinical-database-1.4 --out feas_out
```

| Argument | Default | Meaning |
|---|---|---|
| `--mimic-dir` | (required) | Folder holding the raw MIMIC-III tables |
| `--out` | `feas_out` | Output folder (created if missing) |
| `--seed` | `0` | Seed for KSWIN's random sampling and the shuffled controls |

- **Inputs:** `ADMISSIONS`, `ICUSTAYS`, `DIAGNOSES_ICD` and `PATIENTS`. Files can be `.csv` or `.csv.gz`, and column names can be upper or lower case. No CHARTEVENTS and no benchmark output are needed.
- **Requirements:** Python 3.8+ (for `date.fromisocalendar`), pandas 1.1+ (for `.dt.isocalendar()`), numpy, scipy, scikit-learn and matplotlib.
- **Runtime:** about 4–5 minutes. Most of it is the KSWIN grid: 8 series × 4 settings × 31 runs each (1 real plus 30 shuffled).

**Outputs**

| File | Contents |
|---|---|
| `summary.md` | Every table, with a short reading guide per section |
| `fig1`–`fig5` PNGs | One figure per question (see table above) |
| `series_all.csv`, `series_mv.csv` | The four daily series (364 rows): `slot` and `ref_date` (MM-DD of the reference calendar) |
| `degradation_monthly.csv` | Mean absolute error by era × target × model × month |
| `kswin_grid.csv` | Full KSWIN results, same as section 4 of `summary.md` |
| `mortality_{coarse,fine}_{all,bench}.csv` | The mortality decomposition tables |

---

# Part 1: what the code does

## Constants (top of file)

| Name | Value | Role |
|---|---|---|
| `SUMMER`, `FLU` | {6,7,8}, {12,1,2} | Summer = June–August (pre-train period); winter = December–February (expected flu season) |
| `N_SLOTS` | 364 | Days in the composite year (52 ISO weeks × 7) |
| `LAGS`, `H` | 14, 7 | The forecaster sees 14 past days and predicts 7 days ahead |
| `REFIT_WINDOW` | 90 | A refit uses the most recent 90 days of targets |
| `COOLDOWN` | 14 | After a triggered refit, alarms are ignored for 14 days |
| `KSWIN_GRID` | (30,7), (60,14), (90,14), (90,30) | (window size, stat size) pairs tested, in days |
| `KSWIN_DEFAULT` | (60, 14) | Setting used for the triggered retraining and Fig 4 |
| `KSWIN_ALPHA` | 0.005 | KSWIN significance level (same as river's default) |
| `N_SHUFFLES` | 30 | Shuffled-order control runs per KSWIN setting |
| `TARGETS` | 4 keys | `pi_adm`, `resp_adm`, `census`, `deaths` |
| `ERAS` | `all`, `mv` | All years, or MetaVision stays only |
| `CHAPTERS` | ICD-9 ranges | Primary-diagnosis groups for the mortality split |

## Composite calendar

MIMIC-III shifts each patient's dates by a separate random offset. Weekday and approximate season
are kept; the year is not. The script therefore pools every stay into one composite year.

**Slots.** One slot is one (ISO week, weekday) pair, so there are 52 × 7 = 364 slots. Slot 0 is the
Monday of ISO week 22, which falls around May 28–June 3. The last slot is the Sunday of ISO week 21,
around late May.

**Why ISO weeks instead of calendar dates.** If stays were pooled by month and day, "June 1" would
collect a Monday from one year, a Tuesday from another, and so on, which averages the weekday cycle
away. Pooling by ISO week × weekday keeps every Monday in a Monday slot, so the weekday cycle
survives as a usable feature.

**`_slot_reference()`** builds `SLOT_DATES`, a real calendar date for each slot, using 2001 for ISO
weeks 22–52 and 2002 for weeks 1–21. These dates are only labels, used to name months on the
x-axis and to decide which slots count as summer or winter. They are not patient dates.

| Module-level variable | Meaning |
|---|---|
| `SLOT_DATES`, `SLOT_MONTH` | Label date and month for each of the 364 slots |
| `PRE_END` | Index of the first September slot (96). Slots before it are pre-training, the rest are the stream |
| `MONTH_STARTS` | First slot of each month, for axis ticks (the few late-May slots at index 0 are skipped so the labels don't collide) |

**`slot_index(ts)`** converts a Series of timestamps to slot numbers: `((iso_week − 22) mod 52) × 7 + weekday`. Missing timestamps are dropped. ISO week 53, which occurs in about one year in six, is also dropped; folding it into week 52 would double-count late December, right at flu-season onset. The function returns only the kept slots, so the output can be shorter than the input. It feeds `np.bincount`, so a count series is just `np.bincount(slot_index(times), minlength=364)`.

**`calendar_index(ts)`** gives a calendar-date composite day (0–364, where 0 = June 1), mapping
Feb 29 to Feb 28. It is used only for the holiday check, where calendar days are the point. Feb 28
is slightly over-counted in leap years, which doesn't matter for a check that only looks at
December, January and July.

**`month_ticks(ax)`, `shade_seasons(ax)`** are plotting helpers. They put month labels on the
x-axis and shade summer (tan) and Dec–Feb (blue).

## Loading

**`_find(d, name)`** locates `NAME.csv` or `NAME.csv.gz` in the folder, ignoring case.

**`_read(d, name, cols, dates)`** reads only the needed columns, upper-cases the column names, and
parses date columns with `errors="coerce"`, so an unparseable date becomes NaT instead of crashing.

**`load(mimic_dir)`** returns four DataFrames:
- `adm`: ADMISSIONS (times, admission type, `HOSPITAL_EXPIRE_FLAG`)
- `icu`: ICUSTAYS (times, `DBSOURCE`, care units, ward ids, `LOS`)
- `pat`: PATIENTS (`DOB`)
- `dx`: DIAGNOSES_ICD (`SEQ_NUM`, `ICD9_CODE`)

## Diagnosis flags and cohort tables

**`diagnosis_flags(dx)`** returns one row per `HADM_ID`:
- `num3`: the first three characters of a numeric ICD-9 code. V and E codes become NaN, so they never match a numeric range.
- `pi`: any diagnosis in 480–488 or 466, in any position. This matches the earlier P&I cohort definition.
- `resp`: any diagnosis in 460–519, in any position. P&I is a subset of this.
- `pi_sub`: the most specific P&I code on the admission, in this priority order: influenza (487–488), viral pneumonia (480), bacterial pneumonia (481–483), unspecified pneumonia (484–486), acute bronchitis (466). An admission with both 486 and 487 counts as influenza.
- `chapter`: the group of the primary diagnosis (`SEQ_NUM == 1`), using `CHAPTERS`. Anything outside those ranges, including V and E codes and missing primaries, becomes "Other".

**`build_tables(adm, icu, pat, dx)`** returns two tables:
- `st`, one row per adult ICU stay:
  - ICUSTAYS joined to PATIENTS and ADMISSIONS.
  - Age is `INTIME.year − DOB.year`, an approximation within one year. Patients over 89 have DOBs about 300 years earlier, so they are correctly kept as adults.
  - Rows with age under 18 or a missing `INTIME`/`OUTTIME` are dropped.
  - The diagnosis flags are attached, `DBSOURCE` is lower-cased, and `n_icu_in_hadm` (number of ICU stays in that admission) is added.
- `hadm`: the first ICU stay of each admission. Used for deaths and the mortality analysis, so each admission counts once.

One point to keep in mind: the P&I and respiratory flags are per admission. An admission with two
ICU stays therefore adds two P&I ICU admissions to the series. That is the right unit for ICU demand
(each ICU arrival uses a bed), but it's why `pi_adm` totals can exceed the number of P&I admissions.

## Series

**`census_series(s)`** counts patients in the ICU at noon on each day:
1. For each stay, find the first noon at or after `INTIME`.
2. Count the noons up to `OUTTIME` (capped at 365 days).
3. Expand those noons into individual timestamps (vectorised with `np.repeat`).
4. Map each to its slot and count.

**`build_series(st, hadm, era)`** returns the four daily arrays (length 364) for one era:

| Key | Built from | Counted on |
|---|---|---|
| `pi_adm` | ICU stays with `pi` true | `INTIME` |
| `resp_adm` | ICU stays with `resp` true | `INTIME` |
| `census` | All adult ICU stays | Noon snapshots (see above) |
| `deaths` | Admissions (first ICU stay) with `HOSPITAL_EXPIRE_FLAG == 1` | `DEATHTIME`, or `DISCHTIME` if `DEATHTIME` is missing |

With `era="mv"`, only stays with `DBSOURCE == "metavision"` are kept. Stays marked `"both"` (the
2008 switchover) are in `all` but not in `mv`.

**`signal_to_noise(y)`** measures how large the winter rise is compared with day-to-day noise:

| Column | Formula |
|---|---|
| `summer_mean_day`, `winter_mean_day` | Mean daily value over the June–August and December–February slots |
| `winter_vs_summer_pct` | 100 × (winter mean / summer mean − 1) |
| `snr_daily` | (winter mean − summer mean) / standard deviation of the summer daily values |
| `snr_weekly` | The same on weekly totals. Each of the 52 weeks is assigned to the month of its Thursday |
| `summer_sd_over_poisson` | Summer daily SD / √(summer mean). Pure counting noise would give 1 |

## KSWIN

**`class KSWIN`** is a minimal re-implementation of KSWIN (Raab et al. 2020) with the same decision
rule as river. It keeps a sliding window of the last `window_size` values. On each new value, once
the window is full:
1. Take the last `stat_size` values as "recent".
2. Draw `stat_size` values at random, without replacement, from the older part of the window.
3. Run a two-sample Kolmogorov–Smirnov test (`method="asymp"`).
4. Raise an alarm if p ≤ alpha **and** the KS statistic D > 0.1.
5. After an alarm, shrink the window to the last `stat_size` values, so it must refill before it can fire again.

It requires `window_size ≥ 2 × stat_size`. It is a single-series detector, so no Bonferroni
correction is applied.

**`kswin_alarms(seq, ws, ss, seed)`** runs KSWIN over a sequence and returns the indices where it
fired.

**`kswin_grid(y, seed)`**, for each setting in `KSWIN_GRID`:
1. Runs KSWIN over the whole composite year in order (pre-training slots first, then the stream).
2. Builds the control: keeps the pre-training slots as they are, shuffles the order of the stream slots, and reruns. This is repeated 30 times.
3. Reports `alarms_pretrain`, `alarms_stream`, `alarms_dec_feb`, `first_stream_alarm` (as a reference date), and the control's `shuffled_mean` and `shuffled_p95` (stream alarms only).

## Degradation proxy

This is a ridge regression standing in for the LSTM. It exists only to show whether there is any
degradation for retraining to recover.

**`_x(y, t)`** builds the feature vector at "now" = t: the 14 values `y[t−13 … t]`, plus a one-hot
for the weekday of the target day `t+7` (21 features in all).

**`_fit(y, taus)`** fits `Ridge(alpha=1.0)` to predict `y[τ]` from `_x(y, τ−7)`, for each target day
τ in `taus` that has 14 days of history.

**`degradation_proxy(y, seed)`** runs a prequential (predict-then-learn) loop:
- **Static model:** fit once, on all targets before September.
- **KSWIN warm-up:** the detector is fed the values seen before the first stream prediction.
- **Loop:** for each target day τ from September 1 to the end, with "now" t = τ − 7:
  - **Monthly:** when t crosses into a new month, refit on targets in [t−89, t]. That gives 9 refits from September to May.
  - **Triggered:** feed `y[t]` to KSWIN. If it fires and no cooldown is running, refit on [t−89, t] and start a 14-day cooldown. Alarms during the cooldown are counted by KSWIN (its window still resets) but don't trigger a refit.
  - **Persistence:** predict `y[τ] = y[t]`, the same weekday one week earlier.
  - Record each model's absolute error for target τ.
- **Returns:** the per-day errors, the monthly refit count, the triggered refit count and the trigger times.

Refits only use targets up to t, meaning values already observed by "now", so nothing leaks from
the future. Label delay is ignored: P&I and respiratory counts are treated as known on the day they
happen, which a live system wouldn't have (see Part 2, section 3).

## Mortality decomposition

**`mortality_frames(hadm)`** adds these columns to the one-row-per-admission table:
- `season`: summer, winter or other, by the month of the first ICU `INTIME`
- `died`: from `HOSPITAL_EXPIRE_FLAG`
- `pi_group`: P&I or non-P&I
- `dx_group`: "P&I (any position)" if P&I, otherwise the primary-diagnosis chapter

It returns two cohorts:
- **All adult ICU admissions.**
- **Benchmark-like:** one ICU stay in the admission, no transfer (same first and last care unit and ward), and LOS ≥ 2 days. This approximates the mimic3-benchmarks in-hospital-mortality cohort. It is not identical, so expect close but not exact agreement with your earlier numbers.

**`kitagawa(df, group_col)`** splits the winter-minus-summer change in overall mortality into two
parts per group g. Writing `s` for a group's share of admissions and `m` for its mortality rate:

- `mix_pts`  = 100 × (s_winter − s_summer) × (mean(m_summer, m_winter) − m̄)
- `rate_pts` = 100 × (m_winter − m_summer) × mean(s_summer, s_winter)
- `total_pts` = `mix_pts` + `rate_pts`

Here m̄ is the average of overall summer and winter mortality. Subtracting m̄ is what makes each
group's mix term readable. Shares always sum to 1, so share changes are zero-sum; without centring,
one group would always show a negative mix term just to offset another. Centring changes no totals.
Summed over all groups, `mix_pts` + `rate_pts` equals the total change exactly.

`p_rate` is a chi-square test (scipy's default 2×2 Yates correction) of season × died within the
group. It tests whether that group's own mortality changed.

## Reporting helpers and `main()`

**`md_table(df)`** writes a DataFrame as a markdown table without needing `tabulate`.

**`roll(y)`** is a centred 7-day mean that wraps around the ends of the composite year, so the curve
has no gaps at the edges.

**`main()`** runs everything in order:
1. Load and build the tables.
2. Build the series for both eras, compute signal-to-noise, draw Fig 1.
3. Run the holiday and weekday checks on ELECTIVE admissions (ADMITTIME, all ages), draw Fig 2.
4. Run the degradation proxy for all eight series, draw Fig 3 (all years only).
5. Run the KSWIN grid, draw Fig 4 (all years, default setting).
6. Run the mortality decomposition for both cohorts, draw Fig 5.
7. Write `summary.md`.

---

# Part 2: how to read the results

## First: sanity checks (about 2 minutes, before reading anything else)

1. **Header line of `summary.md`.**
   - Adult ICU stays should be in the tens of thousands, close to what you know from ICUSTAYS after removing neonates.
   - P&I share of stays should be near the roughly 19–22% you saw before.
   - If it's far off, the diagnosis join or the age filter went wrong.
2. **MetaVision ÷ all-years ratio.** For the three count series, `mv` summer means should be roughly 0.35–0.45 of `all`, since MetaVision covers about 4–5 of roughly 12 years. A much smaller ratio means `DBSOURCE` values aren't what the script expects.
3. **Units.** Every count is a composite: about 12 years (all) or 4–5 years (mv) stacked into one. Dividing by those factors gives a rough "one real ICU" scale. Use that when describing magnitudes, never the raw composite numbers.

## 1. Signal vs. noise (section 1, Fig 1)

| Column                   | How to read it                                                               | Rough guide                                                                                                            |
| ------------------------ | ---------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------- |
| `winter_vs_summer_pct`   | Size of the seasonal rise                                                    | Positive for P&I and respiratory if the Week 1 seasonality plot holds. Census and deaths may be small or even negative |
| `snr_weekly`             | Main number. Does the weekly winter level stand clear of week-to-week noise? | > 2 clear · 1–2 marginal · < 1 too weak to drive detection or degradation                                              |
| `snr_daily`              | Same, per day                                                                | Always smaller. With independent noise it's about `snr_weekly / √7` (≈ 0.38×), so don't judge a target on this column  |
| `summer_sd_over_poisson` | Is daily noise just counting noise?                                          | ≈ 1 Poisson-like · > 1.2 extra variation (weekday cycle, clustering) · well below 1 only for census                    |

**What to watch out for**
- **Census** is a running total of overlapping stays, so neighbouring days are strongly correlated. Its SD and SNR don't mean the same thing as for the count series. Read census from Fig 1 (is there a visible winter level shift?) rather than from its SNR.
- **The composite is smoother than reality.** An SNR here is about √12 ≈ 3.5× higher than one real hospital would see for the same seasonal pattern (√(4–5) ≈ 2× for MetaVision). Reviewers will ask about this. A target that only just passes here would be weak in deployment.
- **MetaVision vs all years.** If `mv` weekly SNR is near or below 1 while `all` is clearly above 2, that is your evidence for gently pushing back on the MetaVision-only restriction. If both pass, the advisor's choice costs little.
- **Fig 1 shape** matters as much as the number. A clean rise from November to February that falls back in March is the ideal. A single spike, or a rise that starts in October, points to the 2009 H1N1 wave landing in October–November of the composite year (a limitation already listed in the research plan).

## 2. Date-shift checks (section 2, Fig 2)

**Holiday table.** `ratio` = elective admissions on the holiday ÷ the mean of control days (Dec 11–18 plus Jan 8–15 for Dec 25 and Jan 1; Jun 20–27 plus Jul 11–18 for Jul 4).

| Ratio | Meaning | Consequence |
|---|---|---|
| < 0.5 | Exact calendar days survive the shift | Daily series and a 7-day horizon are justified |
| 0.5–0.85 | Partial smear, a few days | A 7-day horizon is fine, but say the seasonal timing is approximate to within days |
| ≈ 1 | Dates smeared by about a week or more | Consider weekly totals with a 1-week horizon. Day-level timing (for example, detection delay in days) shouldn't be claimed |

**What to watch out for**
- **Noise.** The ratio rests on single-day counts. With c elective admissions per composite day, its standard error is roughly 1/√c. At about 20 per day, that's ±0.2, so only a ratio below about 0.5 is convincing on its own. Look at the bar chart: a real holiday effect is a clear gap on the exact day, not one slightly short bar.
- **Dec 25 and Jan 1 should agree.** If only one dips, treat it as noise.
- **Jul 4** has fewer electives around it and is the weakest of the three checks.

**Weekday panel.** Elective admissions should drop sharply on Saturday and Sunday. Under a uniform split, the weekend would be 28.6% of admissions; electives are usually far below that. A flat profile would mean weekdays were not preserved, which contradicts the MIMIC documentation, so recheck the parsing before believing it.

## 3. Degradation proxy (section 3, Fig 3)

| Column | How to read it | Rough guide |
|---|---|---|
| `MAE% static/monthly/triggered/persistence` | Stream mean absolute error as % of the stream mean | Compare across models within a row, never across targets (census looks small only because its level is large) |
| `static winter/Sep-Oct MAE` | Does the summer-trained model get worse in flu season? | ≥ 1.3 real degradation, the paper's premise holds · 1.0–1.3 weak · ≤ 1 none, so retraining has nothing to recover |
| `refits monthly` | Always 9 (September through May) | A different number would be a bug |
| `refits triggered` | How often KSWIN asked for a refit | 0 → triggered is identical to static, so read section 4 to see why |

**How to read Fig 3**
- **Static (grey)** should track the others in September–October, then pull away from December to February if degradation is real.
- **Monthly (navy)** is the upper bound on what refitting can achieve at that cost.
- **Triggered (red)** is the claim. The best case is that it follows monthly through winter with far fewer refits. A useful single number for the report is the recovery share, (static − triggered) / (static − monthly), computed on Dec–Feb MAE from `degradation_monthly.csv`.
- **Persistence (dashed)** is the bar to beat. If persistence is about as good as the refitted models, the series is mostly level plus noise and the lag features already adapt. That weakens the case for retraining, and the report should say so honestly.

**What to watch out for**
- **Lag features soften degradation.** A ridge model whose inputs are recent counts partly follows a level change even without refitting, so this proxy may understate degradation. An LSTM trained on inputs normalised to summer can degrade more, because winter values fall outside its training range. Treat a weak result here as "not proven", not "absent".
- **Month-level MAE is noisy.** Each point is about 30 errors from a single run. Differences under about 10–15% between models within a month aren't meaningful.
- **Label delay is ignored**, which is optimistic for `pi_adm` and `resp_adm`, whose flags arrive at discharge. Census and deaths don't have this problem.
- **September is identical by design.** All refitting models still use summer-dominated windows there.

## 4. KSWIN on the series (section 4, Fig 4)

| Column | How to read it |
|---|---|
| `alarms_pretrain` | False alarms in summer, which is assumed stable. Should be 0 or close to it |
| `alarms_stream` | Alarms from September to May, in the real order |
| `alarms_dec_feb` | Of those, how many fall in December–February |
| `first_stream_alarm` | When the detector first reacts (a reference date) |
| `shuffled_mean`, `shuffled_p95` | Stream alarms when the stream's order is shuffled |

**What counts as a good result:** `alarms_stream` above `shuffled_p95`, with `first_stream_alarm` between about late October and December (onset) and/or alarms around March (offset), and few pre-training alarms.

**What the shuffled control tests.** Shuffling keeps the stream's values but destroys their order.
The shuffled stream still differs from summer as a whole, so the control can also fire. The
comparison therefore asks whether the real ordering produces a well-timed onset, not merely
whether winter differs from summer:
- Real ≈ shuffled: alarms come from a general level difference, not a detectable onset.
- Real well above shuffled: the timing carries information.

**What to watch out for**
- **Census will over-alarm.** The KS test assumes independent samples, and neighbouring census days are strongly correlated. Census alarms say little about seasonality; prefer the count series for detection claims.
- **Integer ties.** Daily counts repeat values, so KS p-values are approximate (usually conservative).
- **Stat sizes and weekdays.** Stat sizes of 7 and 14 each contain whole weeks, so weekday mix doesn't bias the test. Stat size 30 doesn't, which adds a little weekday noise.
- **Small stat sizes have low power.** The (30, 7) setting will often show 0 alarms everywhere. That's expected and doesn't mean the series has no shift.
- **Thirty shuffles is coarse.** `shuffled_p95` falls between the 2nd- and 3rd-highest of 30 runs. A margin of 1 alarm isn't convincing; a margin of several is.
- **Contrast with Oct 14.** Patient-level KSWIN there needed stat sizes of about 500–2,400 stays. If day-level windows of 30–90 now give well-timed alarms, that is the main detection argument for the pivot.

## 5. Mortality decomposition (section 5, Fig 5)

**Step 1: pick the cohort.** Compare each cohort's overall line with your earlier figures (0.125 → 0.146, p = 0.0018). Use whichever cohort matches more closely. The benchmark-like one should be nearer, but won't match exactly.

**Step 2: coarse table (P&I vs non-P&I).**
- The earlier estimate was that about 80% of the rise comes from non-P&I `rate_pts`, with case mix about 13% and P&I's own rate about 4%.
  - **Confirmed** if non-P&I `rate_pts` is most of `total_pts` and its `p_rate` is small: the winter excess isn't mainly a flu story.
  - **Revised** if P&I `mix_pts` is large instead: more P&I admissions carry the rise, which supports the P&I framing.
- The header line also gives total mix vs total rate across the fine groups.

**Step 3: fine table (primary-diagnosis groups).**
- Name the one or two groups with the largest positive `rate_pts`, but only those with n in the hundreds per season and a small `p_rate`.
- There are 9 groups, so use a stricter cut-off than 0.05. About 0.005 (0.05 / 9) is a reasonable bar.
- "Other" is a catch-all (V and E codes, unusual primaries). Don't build a story on it.
- Circulatory and respiratory rises are the clinically plausible ones, since both are known to peak in winter.

**Step 4: P&I subtype table (your viral-vs-bacterial idea).**
- Expect unspecified pneumonia (484–486) to hold most P&I admissions. If so, the codes can't really separate viral from bacterial, and the report should say that in one sentence.
- Viral (480) and influenza (487–488) groups may have under 100 admissions per season. A mortality rate on 100 admissions carries roughly ±8 points of uncertainty, so don't compare single-group rates.
- If a comparison is needed, pool viral and influenza against bacterial.

**What to watch out for**
- **Season** is the month of the first ICU `INTIME`. A December admission that dies in January counts as winter.
- **Primary diagnosis** for the fine groups is `SEQ_NUM == 1`, which is a billing order, not always the clinical reason for ICU admission.
- **What it means for the paper.** If non-P&I patients with similar measured features die more often in winter, that hints at a change in P(y|x). It's worth a sentence, and it's a reason deaths or an acuity measure might be a stronger forecasting target than P&I.

## Putting it together: suggested go / no-go

A target supports the pivot if it meets all four:

1. `snr_weekly` clearly above 1, ideally above 2.
2. `static winter/Sep-Oct MAE` ≥ 1.3.
3. Triggered refitting close to monthly with fewer refits, and better than persistence.
4. KSWIN stream alarms above the shuffled 95th percentile, timed near onset or offset.

These thresholds are working suggestions to adjust once you see the real numbers, not established
standards. If no daily series passes, rerun the reasoning on weekly totals before dropping the
pivot.

## Known limitations (carry into the report)

- **Composite year.** About 12 (all) or 4–5 (MetaVision) seasons are pooled, so single-season severity can't be recovered, and the 2009 H1N1 wave lands in October–November.
- **Density.** The series is about 12× / 4× denser than one real ICU's, so it's smoother than any single hospital's series.
- **Order across patients within a slot is arbitrary.** The forecast is of the pooled seasonal profile.
- **Label delay.** P&I and respiratory flags come from discharge codes and arrive late in a live system.
- **ISO week 53 is dropped**, about 0.3% of stays.
- **The degradation result is a linear stand-in**, not the LSTM.
