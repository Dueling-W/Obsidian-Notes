2026-10-21 11:02

Course: #mth602

## Big Ideas

*quick summary of ideas - 3-5 bullet points max*

## Key Concepts

*place links to full notes here*

## Notes
- *Notes will be uploaded on GitHub ~1 week after class time*
- **Basic least squares problem**
	- $\{t_{i},y_{i}\}^N_{i=1}$, N observations at points (t, y)
	- $y(t_{i};\vec{w}) = \sum^M_{i=0}w_{i}\phi_{i}(t)$
	- $\vec{y}_{M}=y(\vec{t}_{i};\vec{w})=Aw$
	- New notation: $\phi$, basically means we can have any collection of functions, not just: $1, t, t^2,t^3, \dots$
		- This is called the basis functions
	- $$
A=
\begin{pmatrix}
\phi_{0}(t_{1}) & \phi_{1}(t_{1}) & \dots & \phi_{M}(t_{1}) \\
\phi_{0}(t_{2}) & \dots & \dots & \dots \\
\vdots & \vdots & \vdots & \vdots \\
\phi_{0}(t_{N}) & \dots & \dots & \phi_{M}(t_{N})
\end{pmatrix}
$$
	- Basic definitions:
		- $$
\begin{gather}
\vec{r} = \vec{y}_{M}-\vec{y} \qquad \text{residual vector} \\
w_{*}=argmin||\vec{r}(\vec{w})||_{2}^2 \qquad \text{minimizing the squared L2 norm} \\
w_{*}=(A^TA)^{-1}A^T \vec{y} \qquad \text{final definition of optimal weights}
\end{gather}
$$
- **Parameter explanation**
	- *Learnable parameter* --> set from the data, such as our weights, $\vec{w}$
	- *Model hyperparameters* --> $M$, what kind of basis functions
		- Could even have error in the model specification, such as minimizing for a polynomial when it isn't even one
	- Large M values (overfit function) --> usually has really high weights, such as in the hundreds of thousands
- **Regularization introduction**
	- Let's minimize the loss/cost function instead of the pure residual
	- $$
\begin{gather}
J(\vec{w}) = \|\vec{y}-A \vec{w}\|_{2}^2 + \lambda \|\vec{w}\|^2_{2}  \\
w_{*}=\text{argmin}_{\vec{w}}J(\vec{w}) \\
\vec{w}_{*}=(A^TA+\lambda I)A^T \vec{y}
\end{gather}
$$
		- $J$ is our loss function
		- The second term is often called ridge regression or more modernly, "weight decay"
		- The more penalization you do, the more you shrink the weights towards zero
	- Regularization --> better test error at the cost of training error
	- In general, want to search over "decades" of lambda, say, starting at $10^{-16}$ and increasing by a power of 10 from there
- **Reguarlization techniques**
	- Add a new matrix $\Gamma$ in front of $\vec{w}$
	- Example, don't penalize the y-intercept ($w_{0}$):
	- $$
\begin{gather}
\lambda\|\vec{w}\|_{2}^2 \\
\lambda\|\Gamma\vec{w}\|_{2}^2 \\
\Gamma = 
\begin{pmatrix}
0 & 0 & 0 \\
0 & 1 & 0 \\
0 & 0 & 1
\end{pmatrix}
\end{gather}
$$
		- This penalizes only weights $w_{1}\,w_{2}$
	- To review/add in: Lasso regression using L1 norm

## Questions/Gaps/Concerns



## Follow-up 

*actions items to follow-up on (e.g., watch video, re-read notes, hw)*



## References

*link to other notes, attachments, or actual lecture slides*
