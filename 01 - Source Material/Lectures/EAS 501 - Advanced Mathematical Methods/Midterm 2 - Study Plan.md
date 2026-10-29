2026-10-29 08:45

Course: #eas501 

## Exam Facts
- **When:** Monday, Nov 2, 2026, at 5:30 pm
- **Format:** 6 problems, the best 4 are graded, 1 hr 15 min. That works out to about 17 minutes per problem.
- **Allowed:** a calculator (below TI-84 level) and a formula sheet, front and back.
- **Grading:** generous partial credit, so always write the setup and the method.
- **Scope:** linear algebra from the Ch. 8–11 slides (09/23–10/21). This is a clean break from Exam 1's multivariable calculus.

## Topic Map

| Lecture                                                      | Topics                               | Practice exam      | Mock exam |
| ------------------------------------------------------------ | ------------------------------------ | ------------------ | --------- |
| [[Lecture 6 - Gaussian Elimination]]                         | REF/RREF, consistency                | (underlies Q2, Q4) | Q2        |
| [[Lecture 7 - Vectors, Span, and Subspaces]]                 | dot/norm/angle, span, subspace       | —                  | —         |
| [[Lecture 8 - Linear Independence, Bases, and Gram-Schmidt]] | LI tests, basis, Gram–Schmidt        | **Q1**             | Q1a, Q2c  |
| [[Lecture 9 - Best Approximation and Matrix Algebra]]        | best approximation, transpose        | —                  | Q1b       |
| [[Lecture 10 - Determinants and Rank]]                       | det, rank, null space                | **Q2**             | Q2        |
| [[Lecture 11 - Inverses, Cramer, and LU Decomposition]]      | inverse, Cramer, LU                  | **Q3, Q4**         | Q3, Q4    |
| [[Lecture 12 - Eigenvalues and Eigenvectors]]                | char. polynomial, symmetric theorems | **Q5**             | Q5        |
| [[Lecture 13 - Diagonalization and Quadratic Forms]]         | $Q^TAQ = D$, quadratic forms         | **Q6**             | Q5b, Q6   |

**Where you stand:** the practice-exam student solutions are correct on Q1–Q5. Q6 is missing the normalization step. The mock exam adds the topics the practice exam skips: best approximation, a parameter-dependent consistency question, Cramer's rule, a repeated eigenvalue, and quadratic forms.

## Schedule

### Thu 10/29 — Foundations (4.5–5 h)
- [ ] **1:15** Read Lectures 6–9. Work each example by hand *before* reading its solution. Fill in the Big Ideas yourself.
- [ ] **0:40** From a blank sheet, with an 18-minute timer each: practice **Q1** (Gram–Schmidt) and **Q2** (null space and rank). Compare to the student answers.
- [ ] **1:00** Read Lecture 10. Redo L8 Ex 2 and L10 Ex 2 without looking.
- [ ] **0:45** Draft the **front** of the formula sheet (Lectures 6–10).
- [ ] Breaks between blocks.

### Fri 10/30 — Computation drills (aim for 3.5–4 h)
- [ ] **1:00** Read Lecture 11. Redo L11 Ex 1 (inverse) and Ex 2 (LU) without looking.
- [ ] **0:45** Timed: practice **Q3** (LU, 18 min) and **Q4** (4×4 inverse, 25 min).
- [ ] **0:45** Read Lecture 12. Practice the cross-product trick and the trace/det check.
- [ ] **0:20** Timed: practice **Q5** (eigenvalues and eigenvectors, 18 min).
- [ ] **0:30** Add Lectures 11–12 to the formula sheet.
- **If the HW meeting runs long, do this minimum (~1.5 h):** Q3, Q4, and Q5 timed, plus the Test Strategy section of Lectures 11 and 12.

### Sat 10/31 — Off 🎃

### Sun 11/1 — Diagonalization + full mock (4–5 h)
- [ ] **1:00** Read Lecture 13. Redo practice **Q6** completely, including $Q$ normalized and $D$. Redo L13 Ex 2 (repeated eigenvalue).
- [ ] **0:30** Finish the **back** of the formula sheet.
- [ ] Break, at least 20 minutes.
- [ ] **1:15** [[Midterm 2 - Mock Exam]] under real conditions: timer, calculator, your formula sheet, pick 4 of 6.
- [ ] **0:45** Grade it with [[Midterm 2 - Mock Exam Solutions]]. List every error by type: arithmetic, concept, or time.
- [ ] Optional if time remains: attempt the 2 mock problems you skipped, untimed.

### Mon 11/2 — Polish (3 h morning + group session)
- [ ] **1:00** Redo every mock problem where you lost points, from scratch.
- [ ] **1:00** Drill your weakest problem type twice more. Use the worked examples in the lecture notes with different numbers.
- [ ] **0:30** Final formula-sheet pass. Add anything you looked up during the mock.
- [ ] **Group session:** trade problems and explain solutions out loud. Teaching is the best last-day review.
- [ ] Stop heavy work at least 1 hour before 5:30. Eat something.

## Formula Sheet Checklist

**Front (Lectures 6–10)**
- [ ] Row-op rules and how to read consistency from the REF
- [ ] Subspace test (3 conditions); span = $\mathbb{R}^n$ iff $\det\neq0$ for $n$ vectors
- [ ] LI tests: det, more vectors than the dimension, contains $\mathbf 0$, orthogonal set
- [ ] Gram–Schmidt formula; orthogonal expansion $\frac{\mathbf u\cdot\mathbf e_j}{|\mathbf e_j|^2}$
- [ ] Best approximation $\mathbf u_N$, error $\mathbf E$, $|\mathbf E|$, and $\mathbf E \perp \hat{\mathbf e}_j$
- [ ] How row operations change the determinant; triangular det = product of the diagonal
- [ ] Thm 10.5.3 table (no / unique / $(n-r)$-parameter); nullity $= n - r$

**Back (Lectures 11–13)**
- [ ] 2×2 inverse; $A^{-1} = \frac{1}{\det A}\text{adj}A$ (adj is the **transpose** of the cofactor matrix); Cramer
- [ ] LU: multiplier = entry ÷ pivot, goes into $L$ at $(i,j)$; forward then back substitution
- [ ] $\det(\lambda I - A) = 0$; $\sum\lambda = \text{tr}A$; $\prod\lambda = \det A$
- [ ] Cross-product eigenvector trick (3×3, simple $\lambda$)
- [ ] The 4 symmetric-matrix theorems
- [ ] $Q^{-1}AQ$ vs. $Q^TAQ$ (normalize!); Gram–Schmidt inside a repeated eigenspace
- [ ] Quadratic form: off-diagonal = **half** the cross-term coefficient; canonical form; positive definite iff all $\lambda > 0$
- [ ] A fully worked 3×3 orthogonal diagonalization as a template

## Exam-Day Strategy
1. **2 min:** read all six problems and rank them by confidence. Do the most mechanical ones first.
2. **~17 min each.** If you are stuck for more than 5 minutes, write the setup and method (partial credit) and move on.
3. **Leftover time:** start a 5th problem. Only the best 4 count, so it's free insurance.
4. **Last 5 min:** run these quick checks.

| Problem type | 30-second check |
|---|---|
| Gram–Schmidt | pairwise dot products are 0; each length is 1 |
| Null space | $A\mathbf x_i = \mathbf 0$; nullity $= n - r$ |
| LU | last row of $L$ times $U$ = last row of $A$ |
| Inverse | one row of $AA^{-1}$ |
| Eigenvalues | sum = trace, product = det |
| Eigenvectors | $A\mathbf v = \lambda\mathbf v$ |
| $Q^TAQ = D$ | columns are unit length and orthogonal; $D$ order matches $Q$ |
