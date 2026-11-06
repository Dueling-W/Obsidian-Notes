2026-10-26 11:03

Course: #mth602 

## Big Ideas

*quick summary of ideas - 3-5 bullet points max*

## Key Concepts

*place links to full notes here*

## Notes
- **Review on Regularization**
	- *Def*: any modification to the the learning problem such that testing (generalization error) is reduced and the training error (may) increase
	- Finding $w_{*}$ (optimal parameters) is a minimization problem over the error (residual)
	- $$
J(\vec{w}) = \|\vec{y}-A \vec{w}\|_{2}^2+ \lambda\|\vec{w}\|_{2}^2 \quad \lambda \geq 0
$$
	- You have options for regularization
		1. $\|\vec{w}\|_{2}^2$ is weight decay, ridge regression, tikhonov regularization 
		2. $\|\Gamma \vec{w}\|_{2}^2$, allows you to ignore certain weights (when Gamma is all 1's on diagonal, you have option 1) - typical case is you have a 0 in the first spot, meaning you don't penalize the y-intercept
		3. Spectral methods --> you set the gamma to some exponential (not needed for exam)
		4. Physics based --> e.g., Kepler's laws where theta must be a constant
	- *Bias-variance trade-off*
		- L experiments in a least-squares problem
		- Collection: $\{t_{i}^{l}, y_{i}^l\}_{l=1}^N$
		- The collection of times will always be the same, but $y_{i}$ will be different, since you are assuming some random Gaussian noise
			- $$
\text{Model:} \quad \vec{w}^l = \min_{\vec{w}}J(\vec{w}) \to y^l(t;\vec{w}^l) = \sum^M_{i=0}w_{i}^l\phi_{i}(t)
$$
		- On Average, how close is $y^l$ to ground truth signal $s(t)$
			- $$
\begin{aligned}
\text{Average model} &=  \vec{y(t)} = \frac{1}{L}\sum^L_{l=1}y^l(t:\vec{w}^l) \\
\text{Model bias} &= \frac{1}{T}\int^{t_{N}}_{t_{1}}[\vec{y(t)}-s(t)]^2\,dt \\
&= \frac{1}{N} \sum^N_{i=1}[\vec{y(t_{i})}-s(t_{i})]^2 \\
&= \frac{1}{N}\|\vec{\vec{y}}-\vec{s}\|_{2}^2 \quad \text{L2 norm}
\end{aligned}
$$
- **Classification table**

| Problem                   | Data                                                         | Classes                     |
| ------------------------- | ------------------------------------------------------------ | --------------------------- |
| Cat vs. Dog <br>as images | gray-scale so $X \in \mathbb{R}^{N \times N}$                | K=2 (cat or dog)            |
| Signal detection          | $X \in \mathbb{R}^N$                                         | K = 2 (signal or no-signal) |
| Actual cat or dog         | Heterogeneous data (feature set), e.g., ear size, fur length | K = 2 (same thing)          |
- **Classification**
	- *Def*: given K discrete classes find a function ("classifier") that does the mapping
	- $$
\begin{gather}
\text{Classifier: } \mathbb{R}^D \to \mathbb{R}^K \\
\text{Data vector: } \vec{x} \in \mathbb{R}^D \\
\text{Class vector: } \vec{c} \in \mathbb{R}^K
\end{gather}
$$
	- *Discriminator function*
		- Output is exactly a class:
			- $$
\text{ex: } \quad \begin{pmatrix}
0 \\
1
\end{pmatrix} \quad \text{or} \quad \begin{pmatrix}
1 \\
0
\end{pmatrix}
$$
			- Expanded to N cases, where each vector has N-1 zeros and exactly 1 one
			- And each vector is unique
	- *Probabilistic*
		- Output vector: $\vec{p} \in \mathbb{R}^K$
		- $$
\begin{gather}
\vec{p} = (p_{1}, p_{2}, \dots, p_{k}) \\
\sum_{i=1}^N p_{i} = 1 \quad 0 \leq p_{i}
\end{gather}
$$
		- Then, you have to define some kind of decision threshold based on the probabilities to actually say "cat" or "dog"




## Questions/Gaps/Concerns



## Follow-up 

*actions items to follow-up on (e.g., watch video, re-read notes, hw)*



## References

*link to other notes, attachments, or actual lecture slides*
