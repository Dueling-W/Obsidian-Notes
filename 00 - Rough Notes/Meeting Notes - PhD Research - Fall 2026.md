
## 2026.11.19 Meeting
- Move around sections for a Section IV dedicated to drift detection
	- Makes paper more clear
	- The current sub-sections in Section V will be moved around in the paper
		- Dataset descriptions --> case study 
		- Parameter fine-tuning will go into their own section (tuning for LSTM and tuning for CUSUM)
- Case study sections:
	- Section 1 --> Dataset
	- Section 2 --> Drift detection (show a graph with CUSUM scoring against time) and mark when alarms were fired with a vertical line
	- Section 3 --> present accuracy of our triggered model against the static one, show much better accuracy during the winter months
	- Section 4 --> training comparison by # of days with constant real-time training approach
		- Compare accuracy, expect constant to be slightly better, but they both should be comparable in accuracy
		- Then a separate table showing training days per season
			- E.g., constant will train every day in Fall, while triggered will train 0 days
- Paper timeline:
	- End of day on Friday --> send over completed Section 4 (drift with algorithm)
	- Work Monday/Tuesday/Wednesday on rest of draft --> finishing up remaining Section 5, Case Study and parameter fine-tuning work
- No meeting next week

## 2026.11.12 Meeting
- Make sure figures are significantly different from prior papers
	- Look to revised Figure 1 as an example
- Need to create algorithms (target 2-3)
	- 2 algorithms --> triggered retraining with KSWIN and real-time training of LSTM models
	- Possible 3rd algorithm --> specifically just for KSWIN
- Case study count --> 3 (similar to prior papers)
	- 1 --> accuracy comparison with a table, look to journal paper for inspiration
	- 2 --> show that it can follow the seasonal trends in winter-time to spring (November --> March/April)
		- March/April to show the fall-off
		- November to show the rise to winter-time
	- 3 --> cost comparison
		- E.g., real-time training every day takes 280 updates, while our approach only uses 10
- Problems with dataset
	- Day-to-day is not time series currently
		- Current approach basically takes total for a season (e.g., summer) and splits that total up amongst all days randomly
	- Fix it with simulations
		- Get true flu/pneumonia trends month-to-month from a different dataset for the entire nation/New England region
		- Model the trend line based on that data
			- Example: during summer basically flat, then, starts rising in November to early December
			- Flu season: flat and high # of admissions during winter
			- Then, starts to fall off during March
		- Day-to-day should have some level of noise (just like what we had in the visibility paper)
- Paper targets (timeline)
	- Next meeting (November 19th) --> experimental results with improved time series dataset using simulation-based approach
	- Week after (Thanksgiving) --> first complete paper draft
	- Thanksgiving (Nov. 26) through December 7th --> paper revisions, hopefully submit before final exams
- Meeting same time next week 

## 2026.11.05 Meeting
- 9 credits next week due to TA work
	- Classes --> EAS 602, EAS 602/700 (seminar + ethics), EAS 601 (research)
- Daily, weekly, and monthly predictions
	- Next day, next full week total, and next month total
	- Adjust window sizes for each prediction type 
	- Using an average cuts down on noise significantly
		- Even a perfect classifier has ~88% accuracy due to pure noise
- Work on pre-training --> accuracy too low right now, pre-training doesn't do a good enough job
	- Try to improve accuracy using AI tools
- Next week not as busy, want to fill out more of the paper (such as dataset or framework section)
- Meeting same time next week 

## 2026.10.29 Meeting
- Initial experiment goal --> by next week's meeting
	- Metrics can be similar to the prior paper on visibility (with our accuracy metric, MAE, etc.)
- Multiple data points in a day --> better/faster re-training/re-initialization
	- Possible extra features --> temperature in the day, since it gets colder in the winter, leading to more sickness
- Diagrams for general idea of approach; drift detected --> retraining of LSTM --> repeat
- Algorithms for approach: maybe 2-3 algorithms
	- High level of approach
	- More detailed with retraining 
	- Algorithm on KSWIN (drift-detection)
- Useful figures --> time series graph where you can see the drop in accuracy, then, mark the retraining with a vertical red line
- Tight deadline --> December 15th, make sure project timeline takes into account Thanksgiving week and exams
- Meeting same time next week (2pm, Thursday), try to send some initial results over before then

## 2026.10.22 Meeting
- Presented results from the week
	- Statistical test --> definitely true drift from the summer to winter
	- Decent results with basic ridge regression model
		- Used metric is WAPE (Weighted Average Percentage Error), formula is:
			- $$
WAPE = 100* \frac{\sum^n_{t=1}|y_{t}-\hat{y}_{t}|}{\sum^n_{t=1}|y_{t}|}
$$
			- Where y_t is the true value and y_t(hat) is the foretasted/predicted value
		- Baseline performance (predict current P&I admissions for P&I admissions in 7 days) --> 24.19% WAPE
		- Static model (pre-trained only in the summer) --> 28.94% WAPE
			- May not seem that much worse than the static model, but the difference is large
			- Using raw MAE now (which is mean absolute error), this is difference in actual P&I patients between the true/predicted value
			- Static model --> Average of 5 MAE in September + October
				- December-February --> Jumps up to an avg. MAE of 9
				- This corresponds to an 80% relative increase in error
				- In order words, the static model generated 80% more error during Winter compared to Fall
		- Triggered re-training model --> 24.21% WAPE
			- This gains back some of the performance lost from the static model 
			- Importantly, this model has much lower degradation during the winter months
			- It is slightly behind the baseline performance (24.19 vs. 24.21)
			- But such a simple model leaves a ton of room for improvement (it isn't even LSTM)
- Integrate multiple features into the drift detection framework
	- Use some kind of correction for all of them
	- Make sure to present my exact decision threshold (z-score, p-value, etc.)
- Alarm based system (multiple layers of alarms)
- Next deliverable --> introduction + related work draft
- Meeting same time next week


## 2026.10.15 Meeting
- Patient-level features didn't change very much between summer pneumonia patients to winter pneumonia patients
	- Could still keep features in (e.g., just because temperature didn't drift during this summer to winter, doesn't mean it will **never** drift)
	- Dangerous features --> those that are very noisy (could throw off drift detection)
- Want to integrate more features that more explicitly drift between the summer to the winter
	- Example --> number of patients with pneumonia
		- This increases by about 15% from the summer to the winter months (roughly 1000 pneumonia patients to 1200 patients)
		- The percentage increases even more dramatically because the hospital had more patients in the summer months (6-8) compared to the winter months (12-2)
	- Limit to 2008-2012 cohort + maybe try to pull in features from the CDC (for example)
- Overlap from prior papers, but cannot use same sentences, figures, etc.
	- Can still talk about real-time training, but it doesn't need to be as big of a focus as in prior papers
- Two components: drift detection (statistical) + real-time training
	- Real-time training --> can be ported over from prior paper
	- Statistical drift detection --> mostly already done coding, pre-built methods make it very easy to use to
		- To-do --> make sure drift detection weighs all features together
- Possible research option --> combining modern AI with expert systems (a system defined by a knowledge base of rules)
- Meeting same time next week




## 2026.10.08 Meeting
- Concern about per-patient mortality prediction --> accuracy and feasibility
- Maybe can perform a per-population prediction
	- Over time, what is the mortality of the population? Is it currently high or low?
		- Concern --> high-dimensional data because you will probably need to feed in data for *all* the patients
	- Probably specifically for respiratory diseases because flu is just simply too rare
- Three things to check for approach
	- Usefulness of approach
	- Presence of covariate drift, change in P(X), that results in lower accuracy for a static model
		- For example, if we are predicting mortality, should go up
	- Data availability check, such as flu virus not having enough cases on its own
- Research the available options and send over through email
- Meeting same time next week 

## 2026.10.01 Meeting
- Focus on co-variate drift
	- P(Y|X) doesn't actually change
	- But the distribution of the input features --> P(X) changes
	- Co-variate easier to detect compared to concept
- Big picture can start to be worked on soon
	- Big picture --> figures, introduction, and related work
- Flu viruses typically change year-to-year and are seasonal
	- Might be a good disease/virus to focus
	- Need to do some simulation for flu data
		- Real patient data --> MIMIC
		- Flu virus data/labels --> simulated/clustered
	- Drift should be triggered when flu virus "changes"
- Need to analyze flu virus, the P(X)
	- Maybe the symptoms of the flu virus?
		- Easy flu --> lower temperature
		- Bad flu --> higher temperature, runny nose, sore throat, etc.
	- So the impact of the symptoms may change over time
- All of the necessary data might not be there
	- Will need to label the data --> clustering technique
	- What will the labels be?
		- 0 --> don't need to take the flu shot/low risk
		- 1 --> high risk patient, take the flu shot
- Good case study --> show x% of patients swap to having the shot be recommended
	- Even 5% of a change may be significant
- Carefully pick out features to select from MIMIC dataset for this purpose
- Update timeline document weekly
- Next meeting at the same time


## 2026.09.24 Meeting
- Different ways to detect changes
	- Auto-encoder method (more complex)
	- Statistical methods more straightforward
- Element of real-time training:
	- Drift detected --> perform some real-time training to adjust model to new context
	- New idea compared to journal paper --> don't need real-time training all of the time (this also improves efficiency)
- Mixture of experts with the Dempster-Shafer theory
	- Reasoning with uncertainty
	- Possible experts --> multiple models + doctor
		- Combine their opinions to make a prediction
- Send over timeline/plan before next meeting
	- How to make the deadline of the conference paper?
	- What problem are we explicitly solving and why should people care?
- Meeting next week at same time (2 pm)

## 2026.09.10 Meeting
- Look a little bit more into diabetes
	- Need to make sure it is a problem worth solving
	- I.e., it isn't extremely easy to detect the changes --> meaning, early warning is important 
- Worth looking into --> other diseases that are less obvious to provide an early warning
	- But, would also need some possible features to provide an early warning
	- Could still be diabetes, but need to look into it more
- Explainable AI --> may look into an expert system (based on rules) combined with deep learning later on
	- Possibly multiple expert systems --> weigh their opinions using Dempster-Shafer theory --> better and explainable answer
		- Dempster-Shafer theory --> reasoning with uncertainty
- Existing research for at-home detection or hospital detection (assistant to the doctor)
	- And which features we need for each direction 
- Problem --> check paper "conclusion", is it useful or not?
	- E.g., just detecting the flow of COVID-19 severity isn't that interesting
		- We know cases are less severe now
		- But, detecting concept drift and forecasting future years is more interesting
- Meeting same time next week (2pm on Thursday)

## 2026.09.03 Meeting
- Big changes in dataset need to be detected --> such as transition from stage-to-stage of diabetes
	- Could call it "early warning of stage drift"
	- Small changes can be adapted to with real-time training, but for major detection --> need full/partial re-training
- First paper --> check for large changes within the model (concept drift/stage changes)
	- Similar idea to auto-encoder storm paper where you need to verify the change to prevent false positives on pure noise
- Two models
	- Model 1 --> actually predict the diabetes condition
	- Model 2 --> detecting actual drift in the data to determine if the disease will move to a new stage
- Understand the details of the diabetes disease before creating model
- Look into different sufficient models for both tasks --> autoencoder GRU (like the anomaly storm paper) or maybe a more modern transformer architecture
- First published conference paper --> something similar to the anomaly storm detection paper (early warning)
- Possibly target the [ICMI IEEE conference](https://www.icmiconf.com/) again
	- Paper deadline --> December 15th, 2026
	- Conference dates --> May 01 + 02, 2027
- Then, work on extending into a journal paper during next Spring + Fall 2027 semesters
- Meeting minutes --> send over right after meeting


## 2026.08.21 Meeting
- Understand the details of the diabetes disease before creating model
- Different models should be used for different stages
	- Monitoring the signals of diabetes
	- Early detection before the patient goes to the doctor
- Two phases for now:
	- Detecting concept drift in diabetes 
	- Apply different models with real-time training for early detection of diabetes (including worsening)
- For now: focus on concept drift and early detection
- Real-time training is only really necessary when concept drift is actually detected --> used to adapt the model to the
- Thursday afternoon at 2pm



## 2026.08.13 Meeting
- Main topic: choosing dissertation topic and discussion of research papers
- Focus on real concept drift --> function modeling the relation between X and Y, P(Y | X), actually changes
	- Opposed to fake/phony concept drift, where the relationship between X and Y changes, but it is due to a missed feature *e*
- Look into latest journal paper on personal website --> topic is anomaly detection using an auto-encoder







# References
