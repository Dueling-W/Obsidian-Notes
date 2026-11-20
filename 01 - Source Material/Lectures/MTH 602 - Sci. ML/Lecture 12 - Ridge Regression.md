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
	- $\vec{y}_{M}=y(\vec{t}_{i};\vec{w})=A \vec{\omega}$
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
\begin{aligned}
\vec{r} &= \vec{y}_{M}-\vec{y} \qquad \text{residual vector} \\
w_{*}&=argmin||\vec{r}(\vec{w})||_{2}^2 \qquad \text{minimizing the squared L2 norm} \\
w_{*}&=(A^TA)^{-1}A^T \vec{y} \qquad \text{final definition of optimal weights} \\
\vec{y_\text{model}} &= A \vec{\omega_{*}} = A(A^TA)^{-1}A^T \vec{y}
\end{aligned}
$$
		- Project operator: $P = A(A^TA)^{-1}A^T$ project $\vec{y}$ onto range(A)
		- $$
\begin{aligned}
P \vec{r} &= 0 \\
P \vec{y} &= \vec{y_{M}} \\
<\vec{r}, \vec{y_{M}}> &= 0 \text{  (orthogonal)}
\end{aligned}
$$
- **Parameter explanation**
	- *Learnable parameter* --> set from the data, such as our weights, $\vec{w}$
	- *Model hyperparameters* --> $M$, what kind of basis functions
		- Could even have error in the model specification, such as minimizing for a polynomial when it isn't even one
- **Fitting to noise and conditioning**
	- Model becomes overfit to noise, resulting in very poor conditioning
		- $k(A)$ becomes very large, meaning even machine eplison $\epsilon_{M}$ becomes a problem
	- In general, larger M --> more accurate (training) but less stable, and fits anything, including noise
- **Regularization introduction**
	- Strategy --> overfitting manifests as large coefficients ($\vec{\omega}$), lets "penalize" that from happening 
	- Let's minimize the loss/cost function instead of the pure residual
	- Define a new loss function for our problem
		- $$
\begin{gather}
J(\vec{w}) = \|\vec{y}-A \vec{w}\|_{2}^2 + \lambda \|\vec{w}\|^2_{2}  \\
w_{*}=\text{argmin}_{\vec{w}}J(\vec{w}) \\
\vec{w}_{*}=(A^TA+\lambda I)^{-1}A^T \vec{y}
\end{gather}
$$
		- The first term is the size of our usual residual, while the term in front of $\lambda$ is the size of our coefficients
		- The second term is often called ridge regression or more modernly, "weight decay"
		- The more penalization you do, the more you shrink the weights towards zero
	- Regularization --> better test error at the cost of training error
	- In general, want to search over "decades" of lambda, say, starting at $10^{-16}$ and increasing by a power of 10 from there
- **Regularized linear least squares**
	- Our optimal weights:
		- $$
\vec{\omega_{*}} = \min_{\vec{w} \in \mathbb{R}^{M+1}} J(\vec{\omega})
$$
	- has a unique solution:
		- $$
\vec{\omega_{*}} = (A^TA+\lambda I)^{-1}A^T \vec{y}
$$
	- Investigating different $\lambda$
		- Recall that if $\lambda = 0$, then you are finding the optimal solution
			- $$
\vec{\omega_{*}}(\lambda = 0)
$$
			- Because it minimizes the residual
		- If $\lambda > 0$ means that the training error must grow:
			- $$
\|\vec{y}- y(\vec{t};\vec{\omega_{*}}(\lambda = 0))\|_{2} \leq \|\vec{y}- y(\vec{t};\vec{\omega_{*}}(\lambda))\|_{2}
$$
		- When to set $\lambda > 0$?
			- for noisy and/or poorly conditioned problems
			- Hopefully, the generalization error will be smaller, meaning:
				- $$
\begin{gather}
\{t_{i}, y_{i}\}_{i=1}^\hat{N} \\
\|\vec{y}- y(\vec{t};\vec{\omega_{*}}(\lambda))\|_{2} < \|\vec{y}- y(\vec{t};\vec{\omega_{*}}(\lambda = 0))\|_{2}
\end{gather}
$$
				- where $\hat{N}$ denotes that the points are not coming from the training/true data set
- **Choosing optimal hyperparameters ($M, \lambda$)**
	- Given that we have:
		- $$
\begin{aligned}
\text{Training data: } \quad T &= \{t_{i}, y_{i}\}_{i=1}^N \\
\text{Validation data: } \quad V &= \{t_{i}, y_{i}\}_{i=1}^\hat{N}
\end{aligned}
$$
		- where: $T \cap V = \emptyset$
			- meaning they have no intersecting points
	- We want to find hyperparameters that minimize the validation set error
		- $$
(M_{*}, \lambda_{*}) = \min_{(M, \lambda)} \sum^\hat{N}_{i=1} (y_{i}-y_{\text{model}}(t_{i};\vec{\omega_{*}}))^2
$$
		- where the $y_{i}$ and $t_{i}$ are from the validation set, and the optimal weight vector $\vec{\omega_{*}}$ is found through:
			- $$
\vec{\omega_{*}} = (A^TA+\lambda I)^{-1}A^T \vec{y}
$$
			- which uses the $\vec{y}$ training data
	- In a sentence: search for the best $(M, \lambda)$ by minimizing the model error on the validation data by using the optimal coefficients obtained from the training data.

## Questions/Gaps/Concerns



## Follow-up 

*actions items to follow-up on (e.g., watch video, re-read notes, hw)*



## References

*link to other notes, attachments, or actual lecture slides*
