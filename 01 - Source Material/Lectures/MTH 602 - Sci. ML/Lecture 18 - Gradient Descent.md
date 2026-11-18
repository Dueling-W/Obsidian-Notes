2026-11-18 11:21

Course: #mth602

## Big Ideas

*quick summary of ideas - 3-5 bullet points max*

## Key Concepts

*place links to full notes here*

## Notes
- **Gradient Descent**
	- *Basic steps*
		1. Model: $\mathbb{E}(\vec{\mathbf{\Theta}}) = \|y_{NN}-y\|_{2}^2$
		2. Initialize $\vec{\mathbf{\Theta}}$, the parameters
		3. Move:
			1. $$
\begin{gather}
\vec{\mathbf{\Theta}}^{(0)} \to \vec{\mathbf{\Theta}}^{(1)} \to \vec{\mathbf{\Theta}}^{(2)} \to \dots  \\
\mathbb{E}(\vec{\mathbf{\Theta}^{(t+1)}}) < \mathbb{E}(\vec{\mathbf{\Theta}^{(t)}})
\end{gather}
$$
	- *Moving with gradient descent*
		- Gradients tell us how to move through the parameter space
		- Given that:
			- $$
\begin{gather}
\nabla f=\hat{\mathbf{x}} \, \frac{\partial f}{\partial x} = 2\mathbf{x}\mathbf{\hat{x}} \\
f(x) = x^2
\end{gather}
$$
		- $\nabla f$ is a vector that points in the direction of max increase
		- Further away from the minima --> the bigger the step
		- Why do we even need learning rate?
			- Stepping with a size opposite the sign of the gradient is typically very bad, you could end up just oscillating between the sides of the parabola 
		- Principle step: $\text{step} = -\alpha \vec{\nabla f}$
	- *Special cases in gradient descent*
		- Are the neural network models unique?
			- No, example: tanh identity in the textbook
			- Proof:
				- $$
\begin{gather}
\tanh(\omega^{(2)}\tanh(\omega^{(1)}t)) = \tanh(\omega^{(2)}(-1)\tanh(-\omega^{(1)}t))  \\
\omega^{(2)} = -\omega^{(2)}, \quad \omega^{(1)}=-\omega^{(1)}
\end{gather}
$$
			- Known in class as "degeneracies" or a "degenerate model"
		- Is $\vec{\mathbf{\Theta}}_{*}$ a minimum if $\nabla E |_{\vec{\mathbf{\Theta}}_{*}} = 0$
			- First, Taylor expand $\mathbb{E}(\vec{\Theta})$ around $\vec{\mathbf{\Theta}}_{*}$
				- $$
\mathbb{E}(\vec{\mathbf{\Theta}}) = \mathbb{E}(\vec{\mathbf{\Theta}}_{*})+(\vec{\mathbf{\Theta}}-\vec{\mathbf{\Theta}}_{*})^T\nabla E |_{\vec{\mathbf{\Theta}}_{*}} + \frac{1}{2}(\vec{\mathbf{\Theta}}-\vec{\mathbf{\Theta}}_{*})^TH(\vec{\mathbf{\Theta}}-\vec{\mathbf{\Theta}}_{*})
$$
			- The H matrix is the Hessian, which must be $H \in \mathbb{R}^{M \times M}$
				- Along the diagonal components: double partials for each model parameter in $\vec{\mathbf{\Theta}}$
				- Then, the off diagonals basically are every single other possible partial
				- Hessian is also symmetric
			- Rewrite the expression with the knowledge that the gradient at your current model parameters is a minimum (gradient equals 0 there)
				- $$
\mathbb{E}(\vec{\mathbf{\Theta}}) - \mathbb{E}(\vec{\mathbf{\Theta}}_{*}) = \frac{1}{2}(\vec{\mathbf{\Theta}}-\vec{\mathbf{\Theta}}_{*})^TH(\vec{\mathbf{\Theta}}-\vec{\mathbf{\Theta}}_{*})
$$
			- Now, you must check that...
				- H is positive definite
					- $$
\begin{gather}
\mathbf{x}^TH \mathbf{x} \geq 0 \quad \text{for all x} \\
H \vec{u} = \lambda \vec{u} \\
\text{all } \lambda \text{ eigenvalues} \\
\lambda_{i} \geq 0
\end{gather}
$$
					- If all those eigenvalues are positive... then you are at a true minima
					- If any are not positive, unknown
				- Easier to check (quickly): $\max_{\lambda}(-H) = \, ?$
					- If any are positive from this, you are not at a true minimum

## Questions/Gaps/Concerns



## Follow-up 

*actions items to follow-up on (e.g., watch video, re-read notes, hw)*



## References

*link to other notes, attachments, or actual lecture slides*
