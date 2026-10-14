2026-10-13 11:05

Course: #mth602

## Big Ideas
- Shannon entropy, self-information, KL-Divergence, and cross-entropy are all connected to each other.
- Cross-entropy is the sum of Shannon entropy and KL-Divergence.
- Multivariate Gaussian are complicated, but still satisfy many of the same properties as regular Gaussian.
	- Such as normalization --> integral equaling 1 and $E[\vec{x}]=\vec{\mu}$
- Variance is more complicated, and is known as *co-variance* when dealing with D-dimensional Gaussian
- Investigated second order moments

## Key Concepts

*place links to full notes here*

## Notes
- **Review from Information Gain Lectures**
	- **Shannon Entropy**
		- Given a PDF P(x) for a random variable x
		- $$
H[P] = E_{x \sim P}[I(x)] = -E_{x \sim P}[\log_{b}P(x)] = -\int P(x)[\log_{b}P(x)]dx
$$
		- ![[Pasted image 20261013110943.png|393]]
	- **Self-information of observation x**
		- ![[Pasted image 20261013111152.png|464]]
			- Intuition: information gained by observing a probability
			- If something is 100% probable --> no information gain
			- If something is 0% probable --> infinite information gain
		- Message length = # of bits = I(x)
			- Want to send small # of bits when high probability, more bits when low probability event (which is fine, because it is rare)
- **Optimal message sending**
	- Shannon entropy in bits = # of bits to optimally encode a message in expected value
	- $$
\begin{gather}
P(x) = \text{ground truth} \\
Q(x) = \text{another distribution} \\
KL(P || Q)=\int P(x)\left[ \log_{b} \frac{P(x)}{Q(x)} \right]dx=E_{x\sim P}\left[ \log_{2} \frac{P}{Q} \right] \\
= E_{x\sim P}[\log P-\log Q]
\end{gather}
$$
	- So KL divergence is the # of extra bits if you encode your message with Q(x) instead of P(x) (on average)
- **Cross-entropy (loss)**
	- $$
H(P, Q) = E_{x\sim P}[-\log_{2}Q] = H[P]+KL(P||Q)
$$
	- In words, cross-entropy can be re-written as Shannon entropy plus the KL-Divergence
	- What happens when you are minimizing your loss (such as in machine/deep learning)?
		- min H(P, Q) --> really minimizing the KL-Divergence, since $H[P]$ remains constant through different Q's
---
- **1-Dimensional Gaussian (review)**
	- $$
x \sim N(x|\mu,\sigma^2) = \frac{1}{(2\pi \sigma^2)^{1/2}}\text{exp}\left[ -\frac{(x-\mu)^2}{2\sigma^2} \right]
$$
- **D-Dimensional Gaussian Intro**
	- $\vec{x}=\mathbb{R}^D$ is a random vector (instead of variable)
	- $$
\begin{gather}
\mathcal{N}(\vec{x}|\vec{\mu}, \Sigma)=\frac{1}{(2\pi)^{D/2}} \frac{1}{\text{Det}(\Sigma)^{1/2}}\exp \left[ -\frac{1}{2}(\vec{x}-\vec{\mu})^T\Sigma^{-1}(\vec{x}-\vec{\mu}) \right] \\
\det(\Sigma) = \prod^D_{i=1}\lambda_{i}, \text{ where } \lambda_{i}\text{ are eigenvalues of } \Sigma \\
\Sigma \in \mathbb{R}^{D\times D}, \vec{\mu} \in \mathbb{R}^D
\end{gather}
$$
	- Facts:
		- Check for normalization:
			- $$
\begin{gather}
\int_{x_{1}=-\infty}^{\infty}\int_{x_{2}=-\infty}^{\infty}\dots\int_{x_{D}=-\infty}^{\infty} \mathcal{N}(\dots)dx_{1}dx_{2}\dots = 1
\end{gather}
$$
		- Check the expectation value of $\vec{x}$:
			- $$
\begin{gather}
E[\vec{x}] = \vec{u} \\
\text{where: } \vec{x} \sim \mathcal{N}(\vec{\mu}, \Sigma)
\end{gather}
$$
		- Finding the variance is more complicated
- **Outer product** $\vec{x} \otimes \vec{x}$
	- Second-order moments are all pairwise products of the components of $\vec{x}$:
	- $$
x_1x_1,\; x_1x_2,\; x_3x_7,\; x_2x_1,\; \dots,\; x_Dx_D
$$
	- Collected entrywise into the outer product:
	- $$
(\vec{x} \otimes \vec{x})_{ij} = x_i x_j, \qquad \vec{x} \otimes \vec{x} \in \mathbb{R}^{D \times D}
$$
	- $$
\vec{x} \otimes \vec{x} =
\begin{pmatrix}
x_1x_1 & x_1x_2 & \cdots & x_1x_D \\
x_2x_1 & x_2x_2 & \cdots & x_2x_D \\
\vdots & \vdots & \ddots & \vdots \\
x_Dx_1 & x_Dx_2 & \cdots & x_Dx_D
\end{pmatrix}
$$
	- The matrix is symmetric: $x_1x_2 = x_2x_1$ (the circled pair), so $x_i x_j$ and $x_j x_i$ show up as mirror entries
	- Compare with the inner product, which is a scalar (the sum of the diagonal / trace):
$$
\langle \vec{x}, \vec{x} \rangle = \sum_{i=1}^{D} (x_i)^2
$$
- **Second moment of a Gaussian**
	- If $\vec{x} \sim \mathcal{N}(\vec{x} \mid \vec{\mu}, \Sigma)$, then:
		- $$
\mathbb{E}[\vec{x} \otimes \vec{x}] = \vec{\mu} \otimes \vec{\mu} + \Sigma
$$
		- In words, the second moment is the "mean part" plus the covariance
- **Example: $D = 1$**
	- In 1D the outer products collapse to squares:
	- $$
\vec{x} \otimes \vec{x} = x^2, \qquad \vec{\mu} \otimes \vec{\mu} = \mu^2
$$
	- $$
\mathbb{E}[x^2] = \mu^2 + \sigma^2
$$
	- Sanity check with the variance:
	- $$
\begin{aligned}
\mathrm{Var}(x) &\equiv \mathbb{E}\big[(x - \mathbb{E}[x])^2\big] \\
&= \mathbb{E}[x^2] - (\mathbb{E}[x])^2 \\
&= \mu^2 + \sigma^2 - \mu^2 = \sigma^2
\end{aligned}
$$
	- So the Gaussian's $\sigma^2$ parameter really is its variance
- **Covariance**
	- Multivariate version of variance, using the outer product:
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
- **Fact 3:** for $\vec{x} \sim \mathcal{N}(\vec{x} \mid \vec{\mu}, \Sigma)$, D-dimensional Gaussian case,
$$
\mathrm{Cov}(\vec{x}) = \Sigma
$$
	- Same idea as the 1D check: the $\Sigma$ parameter is the covariance matrix


## Questions/Gaps/Concerns



## Follow-up 

*actions items to follow-up on (e.g., watch video, re-read notes, hw)*



## References

*link to other notes, attachments, or actual lecture slides*
