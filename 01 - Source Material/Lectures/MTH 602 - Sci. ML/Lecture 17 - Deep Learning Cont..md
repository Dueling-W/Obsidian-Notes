2026-11-16 11:04

Course: #mth602

## Big Ideas

*quick summary of ideas - 3-5 bullet points max*

## Key Concepts

*place links to full notes here*

## Notes
- **Network diagrams and feed-forward networks**
	- *Inputs and outputs*
		- $$
\begin{aligned}
\vec{t} &\in \mathbb{R}^{D+1} \\
y(t) &\in \mathbb{R}
\end{aligned}
$$
		- All arrows points to each hidden unit, labeled as $z$
			- The result from adding all inputs is equal to $z_{1}$
			- $z_{1}$ is then transformed using some activation function (non-linearity)
	- *Equations for a two-layer neural network*
		- $$
y(\mathbf{t};\vec{\mathbf{\theta}}) = f\left( \sum_{j=1}^M \omega_{j}^{(2)} h\left( \sum^D_{i=0} \omega_{ji}^{(2)}t_{i} \right) \right)
$$
		- This is for a single $y$, in reality you might have $K$ outputs, in that case, the above function would get a k index
		- $$
y_{k}(\mathbf{t};\vec{\mathbf{\theta}}) = f\left( \sum_{j=1}^M \omega_{jk}^{(2)} h\left( \sum^D_{i=0} \omega_{ji}^{(2)}t_{i} \right) \right)
$$
	- *Learnable parameters and residuals*
		- $$
\begin{aligned}
\vec{\mathbf{\Theta}} &= \{\omega^{(1)}, \omega^{(2)}\} \\
\vec{\mathbf{r}} &= \vec{y_{data}} - \vec{y_{NN}} (\vec{t};\vec{\theta}) \\
\vec{\mathbf{\Theta}}_{opt} &= \min_{\vec{\Theta}}\|\vec{r}\|_{2}^2
\end{aligned}
$$
- **Activation functions and hyperparameters**
	- *Activation function choices*
		- Must be...
			1. Non-linear
			2. Continuous
			3. Differential
			4. Computationally efficient
	- *ReLU*
		- Activation function choice, popular
		- Simple function
		- $ReLU(x) = \max(0, \mathbf{x})$
		- Why is it not linear?
			- With a simple example
				- ReLU(-1) = 0
				- ReLU(2) = 2
				- ReLU(-1) + ReLU(2) = 0 + 2 = 2
				- ReLU(-1+2) = ReLU(1) = 1
			- This proves it is a non-linear function
		- Differentiable
			- $$
ReLU(x)' = \\
\begin{cases}
0 & x < 0 \\
1  & x \geq 1
\end{cases}
$$
	- *Universal approximation theorem*
		- Suppose ground truth function is $y(t)$, where $y$ is continuous
			- $$
y_{NN} = (t; \vec{\mathbf{\Theta}}_{opt})
$$
		- Imagine you are claiming the above function is your optimal neural network
			- Therefore, the following inequality should hold:
			- $$
\|y-y_{NN}\|^2_{2} \leq Cm^{-\alpha}
$$
			- $\alpha >0$ and if y is a smooth function, $\alpha =2$
			- Can rewrite it as and take the log:
			- $$
\begin{aligned}
\mathbb{E} &\approx Cm^{-\alpha} \\ 
\log \mathbb{E} &\approx \log(Cm^{-\alpha}) \\
&= \log C - \alpha \log m
\end{aligned}
$$
			- What you should get on a log-log plot...
				- is a straight line with a negative slope, where that slope is $-\alpha$
			- 

## Questions/Gaps/Concerns



## Follow-up 

*actions items to follow-up on (e.g., watch video, re-read notes, hw)*



## References

*link to other notes, attachments, or actual lecture slides*
