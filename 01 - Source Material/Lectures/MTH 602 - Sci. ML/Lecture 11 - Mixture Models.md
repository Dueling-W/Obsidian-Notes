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
Q(\vec{x}) = (\vec{x}-\vec{\mu})\Sigma^{-1}(\vec{x}-\vec{\mu})
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
		 - Case c) is the one we discussed where the identity matrix is involved, while case b)
		 - Case b) involves stretching the Sigma matrix, similar to the 1-D case where you approach a flat line
 - **Facts about $\Sigma$**
	 - $\Sigma^{-1}$ is a positive definite matrix:
		 - $Q(\vec{x}) = \vec{x}^T\Sigma^{-1}\vec{x} \geq 0$ for $\forall \vec{x} \in \mathbb{R}^D$
	 - $\lambda$ are real, $\lambda > 0$
	 - $\Sigma$ and $\Sigma^{-1}$ are symmetric
	 - Visualization of 2-D Gaussian on GitHub!
 - **Parametric density estimation: D-Dim Gaussian**
	 - $$
\begin{gather}
N \text{ observations of } \vec{x}, x \in \mathbb{R}^D \\
\vec{\vec{x}} = (\vec{x}_{1}, \vec{x}_{2}, \vec{x}_{3}, \dots, \vec{x}_{N}) \\
\text{each  } \vec{x}_{i} \sim \mathcal{N}(\vec{x}|\vec{\mu}, \Sigma) \\
P(\vec{\vec{x}} | \vec{\mu}, \Sigma) = \prod^N_{i=1} \mathcal{N}(\vec{x}_{i}|\vec{\mu}, \Sigma) = \mathcal{L}(\vec{\mu}, \Sigma) \\
\vec{\mu}_{ML}, \Sigma_{ML} = \max_{\vec{\mu}, \Sigma} \mathcal{L}(\vec{\mu}, \Sigma)
\end{gather}
$$
	- Very similar to the 1-D case. We are are maximizing the likelihood solution over our parameters (those being mu and Sigma)
	- $$
\begin{gather}
\vec{\mu}_{ML} = \frac{1}{N} \sum^N_{i=1} \vec{x}_{i} \\
\Sigma_{ML} = \frac{1}{N} \sum^N_{i=1} (\vec{x}_{i} - \vec{\mu}_{ML})\otimes(\vec{x}_{i} - \mu_{ML})
\end{gather}
$$
		- These are estimates for each parameter; good question to ask: how good are our estimates?
- **Estimation bias**
	- bias of parameters = $\mathbb{E}[\theta_{*}] - \theta_{true}$
	- put text from images here regarding bias!!
- **Mixture models for density estimation**
	- $$
P(\vec{x}) = \sum^K_{i=1}\Pi_{i}P_{i}(\vec{x}) = \sum^K_{i=1}P(\vec{x}|i)P(i)
$$
	- P(i) is your probability of the data your are looking at coming from i
	- First part is the weighted sum version and just a different way of looking at the problem vs. the probability version
- **Specifying to Gaussian Mixture Models (GMM)**
	- Again, N observations using the stacked vector notation used earlier in notes
	- Likelihood: 
	- $$
\begin{gather}
P(\vec{\vec{x}} | K, \{\Pi_{i}\}^K_{i=1}, \{\vec{\mu}_{i}, \Sigma_{i}\}^K_{i=1}) \\

\end{gather}
$$
		 - Using all of the data we have with $\vec{\vec{x}}$
		 - The pi's are the weighting values for each distribution, and the final section are the actual Gaussian parameters for each
		 - 


## Questions/Gaps/Concerns



## Follow-up 

*actions items to follow-up on (e.g., watch video, re-read notes, hw)*



## References

*link to other notes, attachments, or actual lecture slides*
