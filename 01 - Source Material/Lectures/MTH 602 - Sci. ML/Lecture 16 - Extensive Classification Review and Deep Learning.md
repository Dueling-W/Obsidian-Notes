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
	- *Different covariances: $\Sigma_{1} \neq \Sigma_{2}$ (scan Ch. 5 p. 14, Fig. 5.14)*
		- The $\vec{\mathbf{x}}^T\Sigma_{k}^{-1}\vec{\mathbf{x}}$ terms no longer cancel in $\alpha$, so $\alpha$ is quadratic in $\vec{\mathbf{x}}$
			- $$
P(c_{1}|\vec{\mathbf{x}}) = \sigma\left(\vec{\mathbf{x}}^T \mathbf{M} \vec{\mathbf{x}} + \vec{b}^T \vec{\mathbf{x}} + c\right) \implies \text{quadratic (curved) decision boundary}
$$
		- 1D case with equal priors (practice Q2): log-likelihood ratio
			- $$
\begin{gather}
\ell(x) = \ln\left[ \frac{P(x|c_{1})}{P(x|c_{0})} \right] = ax^2 + bx + c \\
a = \frac{1}{2\sigma_{0}^2} - \frac{1}{2\sigma_{1}^2}, \quad b = \frac{\mu_{1}}{\sigma_{1}^2} - \frac{\mu_{0}}{\sigma_{0}^2}, \quad c = \frac{\mu_{0}^2}{2\sigma_{0}^2} - \frac{\mu_{1}^2}{2\sigma_{1}^2} + \ln\frac{\sigma_{0}}{\sigma_{1}}
\end{gather}
$$
			- $a = 0$ (equal variances) --> linear equation, one threshold
			- $b^2 - 4ac > 0$ --> two thresholds (narrow class in the middle, wide class on both sides)
			- $b^2 - 4ac < 0$ --> no threshold, one class wins everywhere
			- Identical distributions --> $\ell(x) = 0$ for all x, so the priors alone decide
	- *Benefits of generative models*
		- Reverse Bayes' rule --> $P(x | \text{class})$
			- Generate sythentic data from the class
		- Decide at runtime what the class priors will be
		- Decide on treshold after the model is built 
			- If risk/loss changes over time
		- Combine hetergeneous datasets more easily
- **Deep learning introduction**
	- *Familiar in some ways...*
		- Same ML tasks like regression/classification
		- Writing down a model (refer to prior notes)
		- Write down a cost function like $\|\vec{y}-y_{\text{model}}(\vec{t};\vec{\omega})\|_{2}^2$
		- Minimize cost function for solution $\vec{\omega}_{\text{opt}}$
	- *Different in other ways...*
		- Still some kind of parameterized model, but typically very large and nonlinear
		- Optimizing for the parameters typically requires high performance computing
	- *Curse of dimensionality*
		- Why do we even need large non-linear models?
		- If $\vec{\mathbf{x}} \in \mathbb{R}^D$, then degree M polynomial has $D^M$ coefficients
			- Optimal weights live in: $\vec{\omega} \in \mathbb{R}^{D^M}$ space
		- Not only does the weight space explode, but the pure number of data points themselves do as well:
			- If you need 100 points to sample a function in 1D...
				- you need $100^{17}$ in 17D
		- ![[Pasted image 20261120090600.png]]
	- *Hidden sparsity in deep learning*
		- Data often "lives" in a lower dimensional space/data manifold
			- Image will be something like: $A \in \mathbb{R}^{N \times N}$, resulting in $N^2$ degrees of freedom
			- But images of interest to humans are much lower dimensional
			- This is because the images themselves have high correlations between the pixels, it isn't just random
			- Example below showing the fundamental difference between the entire, random image space and natural images
			- ![[Pasted image 20261120090931.png|449]]
		- You don't have to tell a deep learning model that specific lower dimensional space, it can find it
		- Netflix challenge example:
			- F(Data) --> lower dimensional "feature space"
			- Data itself is a combination of all users on Netflix/shows/movies/etc. (very high-D)
			- But, the challenge winners showed that you can relate users in with only a few shows/movies
	- Conclusions: many classical algorithms exist for these problems... but some problems can really only be solved well using deep learning models
 
## Questions/Gaps/Concerns



## Follow-up 

*actions items to follow-up on (e.g., watch video, re-read notes, hw)*



## References

*link to other notes, attachments, or actual lecture slides*
