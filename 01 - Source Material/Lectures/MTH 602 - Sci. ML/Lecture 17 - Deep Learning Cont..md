2026-11-16 11:04

Course: #mth602

## Big Ideas

*quick summary of ideas - 3-5 bullet points max*

## Key Concepts

*place links to full notes here*

## Notes
- **Network diagrams and feed-forward networks**
	- *Inputs and outputs*
		- Regression with multilayer network (our classic example)
		- $$
\begin{gather}
\vec{t} \in \mathbb{R}^{D+1} \\
y(t) \in \mathbb{R} \\
\{t_{i}, y_{i}\}^N_{i=1}
\end{gather}
$$
		- All arrows points to each hidden unit, labeled as $z$
			- The result from adding all inputs is equal to $z_{1}$
			- $z_{1}$ is then transformed using some activation function (non-linearity)
	- *Equations for a two-layer neural network*
		- $$
y(\mathbf{t};\vec{\mathbf{\theta}}) = f\left( \sum_{j=0}^M \omega_{j}^{(2)} h\left( \sum^D_{i=0} \omega_{ji}^{(1)}t_{i} \right) \right)
$$
		- Where f and h are activation functions (don't need to be the same)
		- $\omega_{j}^{(2)}, \omega_{ji}^{(1)}$ are parameters learned from the data..
			- $$
\begin{aligned}
\vec{\omega}^{(2)} &= (\omega_{0}^{(2)}, \omega_{1}^{(2)}, \dots, \omega_{M}^{(2)}) \\
\omega^{(1)} &= \begin{pmatrix}
\omega_{00}^{(1)} & \omega_{01}^{(1)} & \dots & \omega_{0D}^{(1)} \\
\omega_{10}^{(1)} & \dots & \dots  & \omega_{1D}^{(1)} \\
\dots & \dots & \dots &  \omega_{MD}^{(1)}
\end{pmatrix}
\end{aligned}
$$
		- This is for a single $y$, in reality you might have $K$ outputs, in that case, the above function would get a k index
		- $$
y_{k}(\mathbf{t};\vec{\mathbf{\theta}}) = f\left( \sum_{j=0}^M \omega_{kj}^{(2)} h\left( \sum^D_{i=0} \omega_{ji}^{(1)}t_{i} \right) \right)
$$
	- *Learnable parameters and residuals*
		- The model in the second line would be a "two-layer neural network" and the hidden layer would contain M+1 "neurons"
		- $$
\begin{aligned}
\vec{\mathbf{\Theta}} &= \{\omega^{(1)}, \vec{\omega}^{(2)}\} \\
y(t;\vec{\mathbf{\Theta}}) &= f(\omega^{T^{(2)}}h(\omega^{(1)}\vec{t})) \\
\vec{\mathbf{r}} &= \vec{y_{data}} - \vec{y_{NN}} (\vec{t};\vec{\theta}) \\
\vec{\mathbf{\Theta}}_{opt} &= \min_{\vec{\Theta}}\|\vec{r}\|_{2}^2
\end{aligned}
$$
        - No closed-form solutions for the optimal model parameters
        - $\vec{\mathbf{\Theta}}$ can be very large (GPTs roughly 5 trillion)
- **Activation functions and hyperparameters**
	- *Model hyperparameters*
		- M: size of hidden layer
		- f, h: what activation functions to use
	- *Activation function choices*
		- Must be...
			1. Non-linear
			2. Continuous
			3. Differentiable
			4. Computationally efficient
	- *Why non-linear? (practice Q5a)*
		- If $h(t) = t$ (linear), the whole network collapses to one affine function:
			- $$
h(\vec{\mathbf{x}}) = \sum_{j=1}^M a_{j}(\vec{\omega}_{j}^T \vec{\mathbf{x}} + b_{j}) + b_{0} = \Big( \sum_{j} a_{j}\vec{\omega}_{j} \Big)^T \vec{\mathbf{x}} + \Big( \sum_{j} a_{j}b_{j} + b_{0} \Big) = \vec{W}^T \vec{\mathbf{x}} + \tilde{b}
$$
			- So the decision boundary $h = 0$ is always a line (hyperplane), no matter how large M is
			- With ReLU, each hidden unit adds a "hinge," so the network builds piecewise-linear boundaries (e.g., the "V" shape, XOR)
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
			- Technically not differentiable at 0
				- Typical choice --> just pick 0 or 1
			- $$
ReLU(x)' = \\
\begin{cases}
0 & x < 0 \\
1  & x > 0
\end{cases}
$$
	       - ReLU is also fast... ref. to AlexNet breakthrough
	- *Universal approximation theorem*
		- Suppose ground truth function is $y(t)$, where $y$ is continuous
			- $$
y_{NN}(t; \vec{\mathbf{\Theta}}_{opt})
$$
		- Imagine you are claiming the above function is your optimal neural network
			- Therefore, the following inequality should hold:
			- $$
\|y-y_{NN}\|_{2} \leq Cm^{-\alpha}
$$
			- Don't square the above error function (RMS $E_{2}$)
			- C is a constant that is > 0, and m are your neurons (also > 0)
			- $\alpha >0$ and if y is a smooth function, $\alpha \geq\frac{1}{2}$ (generally)
				- Expect $\alpha =2$ for a two-layer ReLU neural network (Homework 6 statement)
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

## Questions/Gaps/Concerns



## Follow-up 

*actions items to follow-up on (e.g., watch video, re-read notes, hw)*



## References

*link to other notes, attachments, or actual lecture slides*
