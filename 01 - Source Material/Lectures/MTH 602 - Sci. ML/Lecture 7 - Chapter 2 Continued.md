2026-09-28 11:11

Course: #mth602

## Big Ideas

*quick summary of ideas - 3-5 bullet points max*

## Key Concepts

*place links to full notes here*

## Notes
- Density estimation
	- Observe $X$ which is a random variable
		- Experiment 1 of N observations: $\vec{X}=(X^1,X^2, \dots, X^N)$
		- $X \sim P(X | \vec{\theta})$, X is in some distribution
	- Likelihood function
		- $$
L(\vec{\Theta}) = P(\vec{X}|\vec{\Theta}) = \prod_{i=1}^NP(X=X^i|\vec{\Theta})
$$
	- where, 
	- $$
\vec{\Theta}_{x}=\text{argmax }L(\vec{\Theta})
$$
- Intuition with Gaussian
	- $X \sim N(X|\mu,1)$
	- If you only observed 7, then you must place the mean at 7
	- Maximizing the likelihood involves adjusting the mean and variance of the Gaussian so as to maximize this product
- Mean and variance
	- Given a set of observations X:
	- $$
X \sim N(X | \hat{u}, \hat{\sigma})
$$
	- Look at the mean and variance
	- $$
\begin{gather}
\mu_{ML} = \frac{1}{N} \sum_{i=1}^NX_{i} & E[u_{ML}] = \hat{\mu} \\
\sigma^2_{ML}=\frac{1}{N}\sum_{i=1}^N(X_{i}-\mu_{ML})^2 & E[\sigma^2_{ML}]=\frac{N-1}{N}\hat{\sigma}^2
\end{gather}
$$
	- So, variance is a biased estimate, and is especially bad for small N
- Example problem using a polynomial and Gaussian conditional distribution
	- Given some data: $[t_{i}, y_{i}]_{i=1}^N$
	- Setting up the linear least squares polynomial model
	- $$
\begin{gather}
y_{i}=\hat{y}(t_{i};\vec{w})+n_{i} & \text{, where n is noise} \\
\hat{y}=\sum_{i=o}^Mw_{i}t & \text{, least squares polynomial}
\end{gather}
$$
	- Now, write the likelihood function for y_i
	- $$
y_{i} \sim N(y_{i}|\hat{y}(t_{i};\vec{w}), \sigma^2)
$$
	- Writing out the entire problem:
	- $$
\begin{gather}
\vec{Y}=(Y^1, Y^2, \dots, Y^N) & \text{given observations} \\
P(\vec{Y}) = \prod_{i=1}^NP(Y_{i}) & \text{due to i.i.d.} \\
= \prod_{i=1}^N N(y_{i}|\hat{y}(t_{i};\vec{w}),\sigma^2) \\
= \prod_{i=1}^N \frac{1}{(2\pi \sigma^2)^\left( \frac{1}{2} \right)}\exp\left[ -\frac{(y_{i}-\hat{y}(t_{i};\vec{w}))}{2\sigma^2} \right] & \text{def. of Gaussian}
\end{gather}
$$
	- *fill in notes for the rest of the derivation here from images*
- Bayes' Rule
	- P(X, Y) = P(Y, X)
	- Def. of the product rule
		- P(X, Y) = P(Y | X)P(X)
		- P(Y, X) = P(X | Y)P(Y)
		- $$
P(Y|X) = \frac{P(X|Y)P(Y)}{P(X)}
$$
		- Imagine Y are your model parameters and X is the dataset
		- P(Y) --> prior distribution
		- P(X|Y) --> probability of your dataset given your model parameters 
		- P(X) --> probability of the dataset (evidence), we call it the normalization factor 
- Simple example using Bayes' Rule
	- $$
\begin{gather}
Y = \{\text{"rain", "snow", "sunny"}\} & \text{possibilities} \\
P(Y=\text{"rain"})=P(Y=\text{"sun"})=P(Y=\text{"snow"})= \frac{1}{3} & \text{known probabilities} \\
T=-5C, \text{"cloud"} & \text{observations} \\
P(Y=\text{"rain"}) = \frac{1}{100}
\end{gather}
$$


## Questions/Gaps/Concerns



## Follow-up 

*actions items to follow-up on (e.g., watch video, re-read notes, hw)*



## References

*link to other notes, attachments, or actual lecture slides*
