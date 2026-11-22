2026-11-18 11:21

Course: #mth602

## Big Ideas

*quick summary of ideas - 3-5 bullet points max*

## Key Concepts

*place links to full notes here*

## Notes
- **Gradient Descent**
	- Want to solve the optimization problem for $\vec{\mathbf{\Theta_{*}}}$
	- Use a variant of gradient descent to "walk towards" optimal solution $\vec{\mathbf{\Theta_{\text{opt}}}}$
	- *Basic steps*
		1. Model: $\mathbb{E}(\vec{\mathbf{\Theta}}) = \|y_{NN}-y\|_{2}^2$
		2. Initialize $\vec{\mathbf{\Theta}}$, the parameters
		3. Move (step or epoch):
			1. $$
\vec{\Theta}^\tau = \vec{\Theta^{\tau-1}} - \eta \nabla_{\Theta}\mathbb{E}|_{\vec{\Theta}^{\tau-1}}
$$
			2. $$
\begin{gather} 
\vec{\mathbf{\Theta}}^{(0)} \to \vec{\mathbf{\Theta}}^{(1)} \to \vec{\mathbf{\Theta}}^{(2)} \to \dots \to \vec{\mathbf{\Theta}}_{\text{end}}  \\
\mathbb{E}(\vec{\mathbf{\Theta}^{(t+1)}}) < \mathbb{E}(\vec{\mathbf{\Theta}^{(t)}}) \\
\text{Hopefully... } \vec{\mathbf{\Theta}}_{\text{end}} \approx \vec{\mathbf{\Theta}}_{\text{opt}} = argmin_{\vec{\mathbf{\Theta}}} \mathbb{E}(\vec{\mathbf{\Theta}})
\end{gather}
$$
       - What can go wrong ($\vec{\Theta}_{\text{end}} \neq \vec{\Theta}_{\text{opt}}$): local minima, non-convergence, slow convergence
	- *Moving with gradient descent*
		- Gradients tell us how to move through the parameter space
		- At a point $\vec{\mathbf{\Theta}}_{p}$ the vector field $\nabla_{\Theta}E(\vec{\Theta})|_{\vec{\Theta}=\vec{\Theta}_{p}}$ points in the direction of maximum function increase
			- Move in the direction of $-\nabla_{\Theta}E(\vec{\Theta})$
			- Scale this step size by the learning rate $\eta > 0$
				- Typically, you want to select $\eta < 1$
		- Given that:
			- $$
\begin{gather}
\nabla f=\hat{\mathbf{x}} \, \frac{\partial f}{\partial x} = 2\mathbf{x}\mathbf{\hat{x}} \\
f(x) = x^2
\end{gather}
$$
		- $\nabla f$ is a vector that points in the direction of max increase
			- ![[Pasted image 20261120100004.png]]
			- Visualization above
			- The red lines are the computed gradient, and the blue lines represent the step at that gradient (scaled by a learning rate)
				- In this case the blue lines are smaller, so $\eta$ must be less than 1
		- Why do we even need learning rate?
			- A full gradient step can overshoot and bounce between the sides of the parabola, so scale it by η.
			- Further away from the minima --> the bigger the step
	- *Example: $E(x) = -x^2$*
		- $\nabla E = -2x\hat{\mathbf{x}}$, so the step $-\eta\nabla E$ points away from $x = 0$
		- $x = 0$ is a stationary point, but an unstable equilibrium (a maximum)
		- Starting exactly at $x = 0$, gradient descent never moves; in practice, floating-point error ($x + \epsilon_{M}$) pushes you off the hill
- **Special cases in neural networks**
	- *Are the neural network models unique?*
		- ReLU example:
			- $M=2, \quad f(x) = 2x, \quad f=h=\text{ReLU}$
			- you can find a 1-parameter family of networks that exactly reproduced $f(x) = 2x$, infinitely many solutions
		- tanh investigation
			- For some activation function, there are $(M!)2^M$ symmetries in "weight space"
			- $M!$ --> swapping (permuting) the hidden units gives the same network, for any activation function
			- $2^M$ --> flipping the sign of each hidden unit's input and output weights gives the same network, for an odd activation like tanh
				- Therefore, $(M!)2^M$ identical solutions
			- For example:
				- $$
\tanh(-\alpha) = -\tanh(\alpha)
$$
				- Now compute:
					- $$
\begin{aligned}
y_{NN}(\vec{t};\mathbf{\Theta}) &= \tanh\left( \sum^M_{j=0}\omega_{j}^{(2)}\tanh\left( \sum_{i=0}^D\omega_{ji}^{(1)}t_{i} \right) \right) \\
&= \tanh\left( -\sum^M_{j=0}\omega_{j}^{(2)}\tanh\left( -\sum_{i=0}^D\omega_{ji}^{(1)}t_{i} \right) \right) \\
&= \tanh\left( \sum^M_{j=0} \hat{\omega}_{j}^{(2)}\tanh\left( \sum_{i=0}^D \hat{\omega}_{ji}^{(1)}t_{i} \right) \right) 
\end{aligned}
$$
					- $$
\begin{gather}
\tanh(\omega^{(2)}\tanh(\omega^{(1)}t)) = \tanh(\omega^{(2)}(-1)\tanh(-\omega^{(1)}t))  \\
\hat{\omega}^{(2)} = -\omega^{(2)}, \quad \hat{\omega}^{(1)}=-\omega^{(1)}
\end{gather}
$$
			- Known in class as "degeneracies" or a "degenerate model"
	- *Is $\vec{\mathbf{\Theta}}_{*}$ a minimum if $\nabla E |_{\vec{\mathbf{\Theta}}_{*}} = 0$*
		- First, Taylor expand $\mathbb{E}(\vec{\Theta})$ around $\vec{\mathbf{\Theta}}_{*}$
			- $$
\mathbb{E}(\vec{\mathbf{\Theta}}) = \mathbb{E}(\vec{\mathbf{\Theta}}_{*})+(\vec{\mathbf{\Theta}}-\vec{\mathbf{\Theta}}_{*})^T\nabla E |_{\vec{\mathbf{\Theta}}_{*}} + \frac{1}{2}(\vec{\mathbf{\Theta}}-\vec{\mathbf{\Theta}}_{*})^TH(\vec{\mathbf{\Theta}}-\vec{\mathbf{\Theta}}_{*})
$$
		- The H matrix is the Hessian, which must be $H \in \mathbb{R}^{N \times N}$ for $\vec{\Theta} \in \mathbb{R}^N$ ($N$ = number of parameters)
			- Along the diagonal components: double partials for each model parameter in $\vec{\mathbf{\Theta}}$
			- Then, the off diagonals basically are every single other possible partial
			- $$
H = \nabla^2 \mathbb{E}(\Theta) = \begin{pmatrix}
\frac{\partial^2E}{\partial\Theta_{1}^2} & \frac{\partial^2E}{\partial \Theta_{1}\partial \Theta_{2}} & \dots & \dots \\
\frac{\partial^2E}{\partial \Theta_{2}\partial \Theta_{1}} & \frac{\partial^2E}{\partial\Theta_{2}^2} & \dots & \dots \\
\vdots & \dots & \ddots\\
\vdots & \dots & \dots & \frac{\partial^2E}{\partial\Theta_{N}^2}
\end{pmatrix}
$$
			- Hessian is also symmetric, meaning $H_{ij}=H_{ji}$
		- Rewrite the expression at a stationary point $\vec{\Theta}_{*}$, where $\nabla E|_{\vec{\Theta}_{*}} = 0$ (whether it is a minimum is what the Hessian test decides)
			- $$
\mathbb{E}(\vec{\mathbf{\Theta}}) - \mathbb{E}(\vec{\mathbf{\Theta}}_{*}) = \frac{1}{2}(\vec{\mathbf{\Theta}}-\vec{\mathbf{\Theta}}_{*})^TH(\vec{\mathbf{\Theta}}-\vec{\mathbf{\Theta}}_{*})
$$
			    - If $\vec{\Theta}_{*}$ is a minimum, then $\mathbb{E}(\vec{\Theta})-\mathbb{E}(\vec{\Theta}_{*}) > 0$, for $\vec{\Theta}$ "close to" $\vec{\Theta}_{*}$
		- Now, you must check the condition on Hessian...
			- $\vec{\Theta}_{*}$ is a minimum if:
				- $$
\begin{gather}
(\vec{\Theta} - \vec{\Theta}_{*})^T [H(\vec{\Theta}_{*})](\vec{\Theta}-\vec{\Theta}_{*}) > 0 \\
\text{for } \quad \vec{\Theta} \approx \vec{\Theta}_{*} + \Delta \vec{\Theta}
\end{gather}
$$
			- $H(\vec{\Theta}_{*})$ must be positive definite for $\vec{\Theta}_{*}$ to be a minimum
				- Same condition as the covariance matrix $\Sigma$ of a Gaussian (Lecture 11): both must be positive definite
				- $$
\begin{gather}
\mathbf{x}^TH \mathbf{x} > 0 \quad \text{for all } x \neq 0 \\
H \vec{u_{i}} = \lambda_{i} \vec{u_{i}} \\
\text{all } \lambda \text{ eigenvalues} \\
\lambda_{i} > 0 \quad \forall \, i=1, 2, \dots,M
\end{gather}
$$
				- If all those eigenvalues are positive... then you are at a true minima
				- If any are not positive, then you know you aren't at a minimum
					- Only undecided when --> $\lambda_{i} = 0$
		- Practical implications
			- Difficult to check the Hessian entirely...
				- Computing eigenvalues is hard and you might have some eigenvalues $\lambda \approx 0$, a.ka. degeneracies in weight space
			-  Easier to check (quickly): $\max_{\lambda}(-H) = \, ?$
				- If this return a positive number, then $H$ has a negative eigenvalue and E (error) can still go lower
			- But in reality... probably just monitor $\|\nabla E\|$ and stop training when it is close to zero

## Questions/Gaps/Concerns



## Follow-up 

*actions items to follow-up on (e.g., watch video, re-read notes, hw)*



## References

*link to other notes, attachments, or actual lecture slides*
