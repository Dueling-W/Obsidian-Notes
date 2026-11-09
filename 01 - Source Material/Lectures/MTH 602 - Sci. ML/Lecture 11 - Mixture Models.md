2026-10-14 11:05

Course: #mth602 

## Big Ideas

*quick summary of ideas - 3-5 bullet points max*

## Key Concepts

*place links to full notes here*

## Notes
- **Review from last class**
	- D-dimensional Gaussian formula:
		- $$
\begin{gather}
\mathcal{N}(\vec{x}|\vec{\mu}, \Sigma)= \\
\frac{1}{(2\pi)^{D/2}} \frac{1}{\text{Det}(\Sigma)^{1/2}}\exp \left[-\frac{1}{2}Q(\vec{x})\right] \\
Q(\vec{x}) = (\vec{x}-\vec{\mu})^T\Sigma^{-1}(\vec{x}-\vec{\mu})
\end{gather}
$$
		- Introduced in Q(x) to help simplify things now
	- Covariance of a vector x
		- $$
\begin{gather} \\
\mathrm{Cov}(\vec{x}) \equiv \mathbb{E}\Big[(\vec{x} - \mathbb{E}[\vec{x}]) \otimes (\vec{x} - \mathbb{E}[\vec{x}])\Big] \\

=\mathbb{E}[\vec{x} \otimes \vec{x}] = \mathbb{E}[\begin{pmatrix}
x^2 & xy \\
yx & y^2
\end{pmatrix}] = \begin{pmatrix}
1 & Cov(xy) \\
Cov(yx) & 1
\end{pmatrix}
\end{gather}
$$
		 - This is used to understand how covariance works between x and y:
		 - ![[Pasted image 20261014112150.png|485]]
 - **More intuition on Q**
	 - $Q(\vec{x})$ is called the Mahalonis distance
	 - Kind of looks like L2-norm, but not quite
	 - Look at a special case: **D = 2**
		 - $$
\begin{gather}
D=2, \vec{\mu} = 0 \\
Q(\vec{x}) = \vec{x}^T\Sigma^{-1}\vec{x} = \vec{x}^T \vec{x} = <\vec{x}, \vec{x}> \\
\text{If sigma is the identity matrix}
\end{gather}
$$
	 - ![[Pasted image 20261014112736.png|498]]
		 - **Figure 3.4:**
			 - **(a)** General Σ gives tilted ellipses.
			 - **(b)** Diagonal Σ gives axis-aligned ellipses.
			 - **(c)** Σ=σ2I gives circles.
		 - With $\mathbf{\Sigma} = \sigma^2 \mathbf{I}$, the quadratic form is:
		 - $$Q = \frac{\Vert{}\mathbf{x} - \boldsymbol{\mu}\Vert{}^2}{\sigma^2}$$
 - **Facts about $\Sigma$**
	 - $\Sigma^{-1}$ is a positive definite matrix:
		 - A matrix $\mathbf{\Sigma}$ being positive definite implies a strict condition on the quadratic form:
		 - $$Q(\mathbf{x}) > 0 \quad \text{for all } \mathbf{x} \ne \boldsymbol{\mu}, \quad \text{and } Q(\mathbf{x}) = 0 \iff \mathbf{x} = \boldsymbol{\mu}$$
		 - In addition, $\det \mathbf{\Sigma} > 0$, which is required for normalization.
	 - $\lambda$ are real, $\lambda > 0$
	 - $\Sigma$ and $\Sigma^{-1}$ are symmetric
	 - Visualization of 2-D Gaussian on GitHub!
 - **Example using $\Sigma$**
	 - $$
\begin{gather}
\Sigma = I \\
\Sigma^{-1} = I \\
Q(\vec{x}) = \sum^D_{i=1} (x_{i}-\mu_{i})^2 \dots \text{Euclidean L2 distance from } \vec{x} \text{ to } \vec{\mu} 
\end{gather}
$$
 - **Parametric density estimation: D-Dim Gaussian**
	 - Multivariate Gaussian, same as Gaussian: sampling, priors, likelihoods, density estimation 
	 - $$
\begin{gather}
N \text{ observations of a random vector } \vec{x} \in \mathbb{R}^D \\
\vec{\vec{x}} = (\vec{x}_{1}, \vec{x}_{2}, \vec{x}_{3}, \dots, \vec{x}_{N}) \\
\text{each  } \vec{x}_{i} \sim \mathcal{N}(\vec{\mu}, \Sigma) \\
P(\vec{\vec{x}} | \vec{\mu}, \Sigma) = \prod^N_{i=1} \mathcal{N}(\vec{x}_{i}|\vec{\mu}, \Sigma) = \mathcal{L}(\vec{\mu}, \Sigma) \\
\vec{\mu}_{ML}, \Sigma_{ML} = \max_{\vec{\mu}, \Sigma} \mathcal{L}(\vec{\mu}, \Sigma)
\end{gather}
$$
	- Very similar to the 1-D case. We are are maximizing the likelihood solution over our parameters (those being mu and Sigma)
	- $$
\begin{gather}
\vec{\mu_{ML}}, \Sigma = \max_{\vec{\mu}, \Sigma} P(\mathbf{\vec{\vec{x}}} | \vec{\mu}, \Sigma) = \dots \text{see book} \\
\vec{\mu}_{ML} = \frac{1}{N} \sum^N_{i=1} \vec{x}_{i} \\
\Sigma_{ML} = \frac{1}{N} \sum^N_{i=1} (\vec{x}_{i} - \vec{\mu}_{ML})\otimes(\vec{x}_{i} - \mu_{ML})
\end{gather}
$$
		- These are estimates for each parameter; good question to ask: how good are our estimates?
- **Estimation bias**
	- $\text{bias}(\vec{\theta}_{*}) = \mathbb{E}[\vec{\theta_{*}}] - \vec{\theta}^{true}$
	- Find that the ML solution is biased (same as 1D)
	- $$
\begin{aligned}
E[\vec{\mu}_{ML}] = \vec{\mu} &\qquad \implies bias(\vec{\mu}_{ML}) = 0 \\
E[\Sigma_{ML}] = \frac{N-1}{N}\Sigma &\qquad \implies bias(\Sigma_{ML}) = \frac{N-1}{N}\Sigma - \Sigma = -\frac{1}{N}\Sigma
\end{aligned}
$$
- **Mixture models for density estimation**
	- Express probability distribution as a sum ("mixture") of simplier distributions ("components")
	- $$
P(\vec{x}) = \sum^K_{i=1}\Pi_{i}P_{i}(\vec{x}) = \sum^K_{i=1}P(\vec{x}|i)P(i)
$$
	- View as a conditional probability
		- $P(k)$ = prior component k
		- $P(\vec{x} | k)$ = probability of $\vec{x}$ from component $k$
	- First part is the weighted sum version and just a different way of looking at the problem vs. the probability version
	- Components are typically parameterized
		- $$
P(\vec{x} | k, \vec{\theta})
$$
		- In which case you find $\vec{\theta}$ by maximizing the likelihood, no longer closed form (expectation maximization)
- **Specifying to Gaussian Mixture Models (GMM)**
	- All components are multivariate Gaussians
	- Again, N observations using the stacked vector notation used earlier in notes
	- Setup:
		- $$
\begin{aligned}
P(\vec{x} | \vec{\theta}, \vec{\pi}_{k}) &= \sum^K_{k=1} \pi_{k} \,\mathcal{N}(\vec{x} | \vec{\theta}_{k}) \\
\text{where } \vec{\theta}_{k} &= (\vec{\mu}_{k}, \Sigma_{k})
\end{aligned}
$$
	- Step by step: 
	- $$
\begin{aligned}
&\text{Make N observations of } \vec{x} \\ 
&\qquad \vec{\vec{x}} = (\vec{x}_{1}, \vec{x}_{2}, \dots, \vec{x}_{N})\\
&\text{Form the likelihood function} \\
&\qquad L(\vec{\theta}_{*}, \vec{\pi}_{*}) = \prod^N_{i=1} P(\vec{x} = \vec{x}_{i} | \vec{\theta}, \vec{\pi}) \\
&\qquad P(\vec{x} = \vec{x}_{i} | \vec{\theta}, \vec{\pi}) = \sum^K_{k=1} \pi_{k} \, \mathcal{N}(\vec{x} = \vec{x}_{i} | \vec{\mu}_{k}, \Sigma_{k}) \\
&\text{Maximize the function} \\
&\qquad \max_{\vec{\theta}_{*}, \vec{\pi}} L(\vec{\theta}, \vec{\pi})
\end{aligned}
$$

## Questions/Gaps/Concerns



## Follow-up 

*actions items to follow-up on (e.g., watch video, re-read notes, hw)*



## References

*link to other notes, attachments, or actual lecture slides*
