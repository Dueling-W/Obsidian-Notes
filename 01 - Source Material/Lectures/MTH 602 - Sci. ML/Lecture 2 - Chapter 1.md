2026-09-09 11:09

Course: #mth602

## Big Ideas

*quick summary of ideas - 3-5 bullet points max*

## Key Concepts

*place links to full notes here*

## Notes
- Notation
	- Professor prefers *t* as the x-axis (so over time) and then $y$ as the y-axis (so observed value at time *t*)
- Polynomial model (almost the same as in book)
	- $$
y_{M}(t, w) = w_{0}+w_{1}t+w_{2}t^2+\dots+w_{M}t^M = \sum_{j=0}^Mw_{j}t^j 
$$
	- Called a linear model (but NOT $y=ax+b$)
- Mark I perceptron
	- Heaviside activation function
	- $$
f(a) = 
\begin{cases}
0,  &  \text{if } a\leq 0  \\
1,  &  \text{otherwise}
\end{cases}
$$
- Defining polynomial model as a network
	- "Features" --> 1 through $t^M$ would be your inputs
	- Then each would have their own associated weights that map to y
- L1, L2, and LP norms (ref. to slides for details)
	- L1 --> pushes points towards the origin 
- Example using the prior defined polynomial model
	- Formal name: linear least squares
	- Given polynomial model $y_{M}(t, \vec{w})$ find $\vec{w}_{*}$, such that:
	- $L^2$ norm of the residual $\vec{r} = \vec{y}-\vec{y}_{M}(\vec{t}; \vec{w})$ is minimized: $\text{min } ||\vec{r}||_{2}$
		- Focus: eventually find $\vec{w}_{*}$ and fix those values, this would result in the function becoming just of t: $y_{M}(t)$
	- Rows = number of datapoints we have of t (observations)
	- Columns = value of $M$ which is the power of the function
	- $$
A= 
\begin{bmatrix}
1 & t_{1} & t_{1}^2 & \dots &  t_{1}^M \\
1 & t_{2} & t_{2}^2 & \dots & t_{2}^M \\
\vdots & \vdots & \vdots & \vdots  & \vdots  \\
1 & t_{N} & t_{N}^2 & \dots & t_{N}^M
\end{bmatrix}
$$
	- $$
\begin{gather} \\
y_{N}(\vec{t};\vec{w}) = A\vec{w} \\
\text{min } ||\vec{r}||_{2} = ||\vec{y}-A\vec{w}||_{2}^2 = f(\vec{w}) \\
\end{gather}
$$
	- Actual steps to solve the minimization problem:
		1. ref. to images 



## Questions/Gaps/Concerns



## Follow-up 

*actions items to follow-up on (e.g., watch video, re-read notes, hw)*



## References

*link to other notes, attachments, or actual lecture slides*
