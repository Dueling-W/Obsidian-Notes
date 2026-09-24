2026-09-14 11:00

Course: #mth602

## Big Ideas

*quick summary of ideas - 3-5 bullet points max*

## Key Concepts

*place links to full notes here*

## Notes
- $A \in R^{N\times(M+1)}$
	- N representing your training points (labeled as $t$)
	- And M+1 represents the M-powers of the model
- Steps from last week:
- $$
\begin{gather} \\
\nabla_{\vec{w}}\lvert \lvert \vec{y}-A \vec{w} \rvert  \rvert_{2}^2  \\
\text{Solve for w* by setting the above equation to 0 (minimization)}
\end{gather} \\
$$
- Gradients
	- $$
\begin{gather}
\vec{x} \in R^N & f(\vec{x}) \text{ be a scalar field} \\
f: R^N \to R \\
3D: f(x, y, z) = f(x_{1}, x_{2}, x_{3}) & \text{better because no letters} \\
\end{gather}
$$
- $\hat{x}_{i}$ are the canonical basis vectors
	- Simple vectors pointing in the different coordinates 
	- $\hat{x}_{1} = (1, 0, 0)$
	- $\hat{x}_{2} = (0, 1, 0)$
	- $\hat{x}_{3} = (0, 0, 1)$
	- And of course their magnitudes are 1
- $$
\begin{gather}
\nabla f(\vec{x}) = \sum_{i=1}^N \hat{x}_{i} \frac{\partial f}{\partial x_{i}}(\vec{x}) \\
\end{gather}
$$
	- What is really happening in the above function?
	- Basically, doing $N$ partial derivatives, so for 2D, it would be 2
- Example:
	- $$
\begin{gather}
2D: \hat{x}(2x)+\hat{y}(2y) \\
\text{if function is } f(x,y)=x^2+y^2
\end{gather}
$$
- Helping with the homework question, tying back to least squares:
	- $$
\begin{gather}
\nabla \vec{w} \lvert \lvert \vec{y}-A \vec{w} \rvert  \rvert_{2}^2 \\
\sum_{n=1}^N[y_i (A-\vec{w})_{i}][y_{i}-(A\vec{w})_{i}]  \\
(y^T-(A\vec{w})^T)(\vec{y}-A\vec{w}) = \vec{y}^T \vec{y}+\vec{w}^TA^TA\vec{w} - 2w^TA^T\vec{y}
\end{gather}
$$
	- You are taking the gradient of $f(\vec{w})$, where $f(\vec{w})$ is the derivation shown above (the long term after the equals sign)
	- When computing the gradient: $2A^TA\vec{w}-2A^\vec{T}y = 0$
	- $$
\begin{gather}
2A^TA\vec{w}-2A^T \vec{y} = 0 \\
2A^TA\vec{w} = 2A^T \vec{y} \\
A^TA\vec{w}_{*}=A^T\vec{y} \\
\vec{w}_{*} = (A^TA)^{-1}A^T\vec{y} \\
r = \vec{y}-\vec{y}_{m}
\end{gather}
$$



## Questions/Gaps/Concerns



## Follow-up 

*actions items to follow-up on (e.g., watch video, re-read notes, hw)*



## References

*link to other notes, attachments, or actual lecture slides*
