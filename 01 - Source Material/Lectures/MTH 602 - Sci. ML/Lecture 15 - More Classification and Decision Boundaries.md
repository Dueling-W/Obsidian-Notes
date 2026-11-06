2026-11-04 11:05

Course: #mth602

## Big Ideas

*quick summary of ideas - 3-5 bullet points max*

## Key Concepts

*place links to full notes here*

## Notes
- **Classification review**
	- Reviewed linear discriminator functions (also called decision boundaries)
	- Example from slides:
		- One line perfectly separates triangle and circle points, this is rare
		- Gaussian example from homework (some misclassifications)
	- "Above" or "below" the decision surface
		- Above --> vector x's inner product with discriminant line is a positive number
		- Below --> vector x's inner product with discriminant line is a negative number
		- Exactly = 0 (you decide)
- **Example problem with linear discriminator**
	- Exam style!
	- Given a well-separated blue and red cluster
	1. Draw a decision surface
		1. Many good choices. Obvious one is just a vertical line on the $x_{1}$ axis, but there is a whole family of good choices
	2. What's the normal $\hat{\omega}$ to this surface?
		1. $\|\hat{\omega}\|_{2}^2 = 1$
		2. Example: $\hat{\omega} = (1, 0)$
			1. It just creates a 90 degree angle with the line. (1, 5) should be perfectly fine as well, for example.
	3. Actual formula:
		-  $$
y(\hat{x}) = (1, 0)\begin{pmatrix}
x_{1} \\
x_{2}
\end{pmatrix}
+\omega_{0}
$$
		- Check: on the surface to find $\omega_{0}$
			- $$
\begin{aligned}
y((1,0)) &= 0 \\
&= (1,0)\begin{pmatrix}
1 \\
0
\end{pmatrix} = 1 \qquad {\text{dot product}} \\
&= 1 + \omega_{0} \\
\omega_{0} &= -1
\end{aligned}
$$
- **Generative Probabilistic Classifier**
	- K classes, denoted as $c_{k}$
	- Joint probability of $\vec{x}$ and $c_{K}$ = 
	- $$
\begin{gather}
P(\vec{x}, c_{k}) = P(c_{k}, \vec{x}) \\
P(\vec{x} | c_{k})P(c_{k}) = P(c_{k} | \vec{x})P(\vec{x}) \\
P(c_{k} | \vec{x}) = \frac{P(\vec{x}|c_{k})P(c_{k})}{P(\vec{x})}
\end{gather}
$$
	- Normalization: $$
\sum_{K} = P(c_{k}|\vec{x}) = 1
$$
		- Sum over all of the classes needs to equal 1
	- Now by substitution, we can get: $$
P(c_{k}|\vec{x}) - \frac{P(\vec{x}|c_{k})P(c_{k})}{\sum_{K}P(\vec{x}|c_{k})P(c_{k})}
$$
	- Let's look at the case for two classes and class = 1:
		- $$
P(c_{k}|\vec{x}) - \frac{P(\vec{x}|c_{1})P(c_{1})}{P(\vec{x}|c_{1})P(c_{1}) + P(\vec{x}|c_{2})P(c_{2})}
$$
	- This entire function can actually be modeled as a simple logistic function
		- Ref to images for proof and paste in plot from book 
		- This specifically works because there are two classes, and you basically bunch up/model the complexity in the $\alpha$ parameter
- **Example using Generative Probability**
	- *Problem set-up*
		- $\vec{x} \in \mathbb{R}^D$
		- $$
\begin{gather}
\text{Class 1} \quad \vec{x} \sim \mathcal{N}(\vec{\mu}_{1}, \Sigma) = P(\vec{x} |c_{1}) \\
\text{Class 2} \quad \vec{x} \sim \mathcal{N}(\vec{\mu}_{2}, \Sigma) = P(\vec{x} |c_{2})
\end{gather}
$$
		- Same Sigma (covariance matrix)
	- *Writing as a logistic function*
		- $$
\begin{aligned}
P(c_{1}|\vec{x}) &= \alpha(\vec{\omega}^T \vec{x} +\omega_{0}) \\
\vec{\omega} &= \Sigma^{-1}(\vec{\mu}_{1}-\vec{\mu}_{2}) \\
\omega_{0} &=
\end{aligned}
$$
		- Need formula for omega from scanned notes
- **Signal vs. Noise Example**
	- *General formula*
		- $$
\begin{aligned}
P(\rho | c_{1}) &= \alpha(\omega \rho + \omega_{0}) \\
\omega &= \Sigma^{-1}(\vec{\mu}_{1} - \vec{\mu}_{2}) = A - 0 = A \\
\omega_{0} &= -\frac{1}{2}A^2 +\ln \left[\frac{P(c_{1})}{P(c_{2})}\right]
\end{aligned}
$$
	- *Specific case*
		- Let $P(c_{1}) = P(c_{2})$
		- $$
\begin{gather}
P(c_{1} | \rho) = \alpha\left( A\rho - \frac{1}{2}A^2 \right)
\end{gather}
$$
		- Optimal $\rho_{*}$
		- $$
\begin{gather}
A\rho_{*} - \frac{1}{2}A^2 = 0 \\
p_{*} = \frac{A}{2}
\end{gather}
$$
	- 

## Questions/Gaps/Concerns



## Follow-up 

*actions items to follow-up on (e.g., watch video, re-read notes, hw)*



## References

*link to other notes, attachments, or actual lecture slides*
