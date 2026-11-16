2026-11-09 11:08

Course: #mth602

## Big Ideas

*quick summary of ideas - 3-5 bullet points max*

## Key Concepts

*place links to full notes here*

## Notes
- **Extended review from prior lectures**
	- *Probabilistic classifiers $\vec{\mathbf{x}} \in \mathbb{R}^D$*
		- $P(c_{1} | \vec{\mathbf{x}})$ = probability of $\vec{\mathbf{x}}$ belonging to class 1
		- $P(c_{2} | \vec{\mathbf{x}}) = 1- P(c_{1} |\vec{\mathbf{x}})$
		- $$
\begin{gather}
P(c_{1} | \vec{\mathbf{x}}) = \frac{P(x | c_{1})P(c_{1})}{P(x|c_{1})P(c_{1}) +P(x|c_{2})P(c_{2})}
\end{gather}
$$
			- $P(x|c_{1})$ is the likelihood function, while $P(c_{1})$ is the prior probability of $c_{1}$
		- Able to write the above Bayes-style formula as a logistic regression formula by multiplying mixed with algebra 
			- $$
\begin{aligned}
P(c_{1}|\vec{\mathbf{x}}) &= \frac{1}{1+\exp(-\alpha)} \\
\alpha &= \ln\left[ \frac{P(\vec{\mathbf{x}}|c_{1})P(c_{1})}{P(\vec{\mathbf{x}}|c_{2})P(c_{2})} \right]
\end{aligned}
$$
			- In other words, the $\alpha$ parameter "bundles" the complexity
			- Posterior --> $\mathbf{\sigma}(\alpha)$
	- *Example using signal detection*
		- Problem setup:
			- $P(c_{1})=P(c_{2})= \frac{1}{2}$, equal probability of signal/no-signal
			- $$
\begin{aligned}
P(x|c_{1}) &= \mathcal{N}(A, 1) = \frac{1}{(2\pi)^{1/2}}\exp\left[ -\frac{1}{2}(x-A)^2 \right] \\
P(c_{1}|\vec{\mathbf{x}}) &= \frac{\exp\left[ -\frac{(x-A)^2}{2} \right]}{\exp\left[ -\frac{(x-A)^2}{2} \right]+\exp\left[ -\frac{x^2}{2} \right]} * \frac{\left( \frac{1}{\exp\left( -\frac{(x-A)^2}{2} \right)} \right)}{\left( \frac{1}{\exp\left( -\frac{(x-A)^2}{2} \right)} \right)} \\
&= \frac{1}{1 + \exp\left[ \frac{A^2}{2} - Ax \right]}
\end{aligned}
$$
		- Specific case when $P(c_{1}|\rho) = 0.5$
			- This case is important because it is when we can't tell if there is a signal or not
			- $$
\begin{aligned}
\frac{A^2}{2} - A\rho &= 0 \\
\rho &= \frac{A}{2}
\end{aligned}
$$
			- Signal has an amplitude at A = 3, so this shows how the optimal $\rho$ gets set to 1.5 
	- *Gaussian example with two means*
		- Problem setup:
			- $$
\begin{aligned}
\vec{\mathbf{x}} &\sim \mathcal{N}(\vec{\mu_{1}}, \Sigma) \quad \text{Class 1} \\
\vec{\mathbf{x}} &\sim \mathcal{N}(\vec{\mu_{2}}, \Sigma) \quad \text{Class 2}
\end{aligned}
$$
		- Finding our $\omega$ and $\omega_{0}$, where $\omega_{0}$ is the offset 
			- $$
\begin{aligned}
P(c_{1}|\vec{\mathbf{x}}) &= \frac{1}{1 +\exp[-(\vec{\omega}^T \mathbf{\vec{x}}+\omega_{0})]} \\ \\
\vec{\omega} &= \Sigma^{-1}(\vec{\mu}_{1}-\vec{\mu}_{2}) \\
\omega_{0} &= -\frac{1}{2} \vec{\mu_{1}}^T\Sigma^{-1} \vec{\mu_{1}} + \frac{1}{2} \vec{\mu_{2}}^T\Sigma^{-1} \vec{\mu_{2}} + \ln\left[ \frac{P(c_{1})}{P(c_{2})} \right]
\end{aligned}
$$
		- Concrete values:
			- $P(c_{1}) = P(c_{2})$
			- $\vec{\mu_{1}} = (0, 0)$
			- $\vec{\mu_{2}} = (1,0)$
			- $\Sigma = \begin{pmatrix}2 & 0 \\ 0 & 1\end{pmatrix}$
				- Being stretched along the $x_{1}$ direction 
		- Draw points/choosing a decision surface
			- Reasonable plot: blue class (0, 0) mean should be at the origin, more stretched along the $x_{1}$ axis
				- Red class (1, 0) should be at the point (1, 0), also stretched along the $x_{1}$ axis
			- Reasonable decision boundary given that: $P(c_{1} | \vec{\mathbf{x}}) = P(c_{2} | \vec{\mathbf{x}}) = \frac{1}{2}$
				- Draw a decision line at point $\left( \frac{1}{2}, 0 \right)$
		- Calculating $\vec{\omega}$ and $\omega_{0}$ with the given values
			- $$
\begin{gather}
\frac{1}{1 +\exp[-(\vec{\omega}^T \mathbf{\vec{x}}+\omega_{0})]} \\
\vec{\omega} \vec{\mathbf{x}} + \omega_{0} \\
\vec{\omega} = \Sigma^{-1}(\mu_{1}-\mu_{2}) =  -\Sigma^{-1} \mu_{2} = \begin{pmatrix}
-\frac{1}{2} \\
0
\end{pmatrix} \\
\omega_{0} = \frac{1}{4}
\end{gather}
$$
			- What is the interpretation of -1/2?
				- This means that you will have arrows pointing to the left, since $\vec{\omega}$ is normal to the decision surface
				- "Above" means to the left of the decision surface/line (positive), and "below" means to the right of the decision surface/line (negative)
	- *Benefits of generative models*
		- Reverse Bayes' rule --> $P(x | \text{class})$
			- Generate sythentic data from the class
		- Decide at runtime what the class priors will be
		- Decide on treshold after the model is built 
			- If risk/loss changes over time
		- Combine hetergeneous datasets more easily
- **Deep learning introduction**
	- Modeling
		- Writing down a model (refer to prior notes), now we have a nonlinear model of many parameters 
	- Residual and minimizing the residuals
		- In linear case, we had the residual function and we just minimized that
		- Now, we need a numerical optimization
- **Curse of dimensionality**
	- Both the number of learnable parameters and needed data points explodes as you move into higher dimensional space
	- But, deep learning can find hidden sparsity
		- Example --> looking for cat images in a 64x64x3 space (RGB),but the actual cat image exists in a lower dimensional version of that space
		- You don't have to tell a deep learning model that specific lower dimensional space, it can find it
 
## Questions/Gaps/Concerns



## Follow-up 

*actions items to follow-up on (e.g., watch video, re-read notes, hw)*



## References

*link to other notes, attachments, or actual lecture slides*
