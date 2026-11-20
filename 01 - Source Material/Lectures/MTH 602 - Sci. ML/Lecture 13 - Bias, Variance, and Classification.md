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
- **Methods of Regularization**
	- Regularization with $\Gamma$
		- $$
J(\vec{w}) = \|\vec{y}-A \vec{w}\|_{2}^2+ \lambda\|\Gamma\vec{w}\|_{2}^2 \quad \lambda \geq 0
$$
		- Penalize all weights (ridge regression):
			- $$
\begin{pmatrix}
1 & 0 & 0 \\
0 & 1 & 0 \\
0 & 0 & 1
\end{pmatrix}
$$
		- Ignore certain weights by index, such as ignore y-intercept
			- y-intercept $\omega_{0}$ only shifts the curve up or down, so penalizing it would pull the fit toward zero for no reason
			- $$
\begin{pmatrix}
0 & 0 & 0 \\
0 & 1 & 0 \\
0 & 0 & 1
\end{pmatrix}
$$
	- LP regularization of weights
		- $$
J(\vec{w}) = \|\vec{y}-A \vec{w}\|_{2}^2+ \lambda\|\vec{w}\|_{p}^p \quad \lambda \geq 0
$$
		- If $p = 1$ --> Lasso regression, gives sparse weights
		- If $p = 0$ --> $\|\vec{\omega}\|_{0}$ = # of non-zero entries of $\omega$
	- Quick regularization summaries 
		1. $\|\vec{w}\|_{2}^2$ is weight decay, ridge regression, tikhonov regularization 
		2. $\|\Gamma \vec{w}\|_{2}^2$, allows you to ignore certain weights (when Gamma is all 1's on diagonal, you have option 1) - typical case is you have a 0 in the first spot, meaning you don't penalize the y-intercept
		3. Spectral methods --> you set the gamma to some exponential (not needed for exam)
		4. Physics based --> e.g., Kepler's laws where theta must be a constant
- **Bias variance tradeoff**
	- Consider doing L experiments in a least-squares problem
		- Collecting data:
			- $$
y^l(t_{i}) = y^l_i = s_{i} + n_{i}
$$
			- where $s_{i}$ is the true signal and $n_{i}$ is the pure noise
		- Solving the regression problem:
			- $$
\begin{aligned}
\vec{\omega}^l &= \min_{\vec{\omega} \in \mathbb{R}^{M+1}} J^l(\vec{\omega}) \\
\text{where } J^l(\vec{\omega}) &= \|\vec{y^l}-A \vec{w}\|_{2}^2+ \lambda\|\vec{w}\|_{2}^2 \\
y^l(t;\vec{\omega^l}) &= \sum^M_{i=0} \omega_{i}^l \phi_{i}(t)
\end{aligned}
$$
			- The "l" denotes the "l'th" experiment collecting data, so, the final line is the model based on the lth experiment
			- $t^l$ will always be the same, since you collect at the same time, but $y_{i}^l$ will vary, since the noise is Gaussian
		- On Average, how close is $y^l$ to ground truth signal $s(t)$
			- $$
\begin{aligned}
\text{Average model} &=  \bar{{y(t)}} = \frac{1}{L}\sum^L_{l=1}y^l(t:\vec{w}^l) \\
\text{Model bias} &= \frac{1}{T}\int^{t_{N}}_{t_{1}}[\bar{{y(t)}}-s(t)]^2\,dt \\
&\approx \frac{1}{T}(\Delta t) \sum^N_{i=1}[\bar{{y(t_{i})}}-s(t_{i})]^2 \\
&= \frac{1}{N}\|\bar{{y}}(\vec{t})-s(\vec{t})\|_{2}^2 \quad \text{L2 norm}
\end{aligned}
$$
			- This result depends on $\lambda$ 
	- By how much does a typical model $y^l$ fluctuate about the mean model $\bar{y}(t)$
		- $$
\begin{aligned}
\text{Variance } &= \frac{1}{L} \sum^L_{l=1} \left[ \frac{1}{T}\int^{t_{N}}_{t_{1}}[y^l(t)-\bar{y}(t)]^2 \, dt \right] \\
&\approx \frac{1}{L} \sum^L_{l=1} \frac{1}{N}\|y^l(\vec{t}) - \bar{y}(\vec{t})\|_{2}^2
\end{aligned}
$$
		- Just like the bias, the variance also depends on $\lambda$
- **Classification table**
	- Goal --> building a map from data to classes

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
		- Classifier maps its data vector to its class vector
	- *Discriminator function*
		- Output is assigned directly to a class
		- Output vector $\vec{c} \in \mathbb{R}^K$:
			- $$
\text{ex: } \quad \begin{pmatrix}
0 \\
1
\end{pmatrix} \quad \text{or} \quad \begin{pmatrix}
1 \\
0
\end{pmatrix}
$$
			- is all zeros expect for the predicted class, which is a one
			- Called 1-of-K coding or one-hot encoding
	- *Probabilistic*
		- Output vector: $\vec{p} \in \mathbb{R}^K$ is a vector of class probabilities
		- $$
\begin{gather}
\vec{p} = (p_{1}, p_{2}, \dots, p_{k}) \\
\sum_{i=1}^K p_{i} = 1 \quad 0 \leq p_{i}
\end{gather}
$$
		- Then, you have to define some kind of decision threshold based on the probabilities to actually say "cat" or "dog"




## Questions/Gaps/Concerns



## Follow-up 

*actions items to follow-up on (e.g., watch video, re-read notes, hw)*



## References

*link to other notes, attachments, or actual lecture slides*
