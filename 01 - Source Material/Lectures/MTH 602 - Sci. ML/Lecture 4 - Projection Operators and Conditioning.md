2026-09-16 11:00

Course: #mth602

## Big Ideas
- A projector satisfies $P^2 = P$, and an orthogonal projection leaves a residual orthogonal to what it keeps
- Conditioning describes the *problem* (how sensitive it is to input perturbations); stability describes the *algorithm*
- The condition number of a matrix bounds how much relative input error gets amplified: $\kappa(A) = \|A\|\,\|A^{-1}\|$
- For least squares, the pseudoinverse $A^+$ plays the role of $A^{-1}$, so $\kappa(A^+)$ controls error in $\vec{w}_*$

## Key Concepts

*place links to full notes here*

## Notes

**Model recap**
- Straight-line model with $w_0, w_1 \in \mathbb{R}$:
 - $$
y_m = w_0 + w_1 t
$$
	- Picture: the data $\vec{y}$, the model $\vec{y}_m$, and the residual $\vec{r}$ form a right triangle

**Projection (linear algebra review)**
- $P$ is a projector from a vector space onto itself (or a subspace):
 - $$
P \cdot P = P \qquad \Longleftrightarrow \qquad P(P\vec{v}) = P\vec{v}
$$
	- Projecting twice does nothing new
	- ![[Pasted image 20261014164432.png|522]]

**Example: projecting $\mathbb{R}^3$ onto the $x_1x_2$-plane**
$$
\vec{v} = \begin{pmatrix} x_1 \\ x_2 \\ x_3 \end{pmatrix} \in \mathbb{R}^3, \qquad
P = \begin{pmatrix} 1 & 0 & 0 \\ 0 & 1 & 0 \\ 0 & 0 & 0 \end{pmatrix}
$$
$$
P\vec{v} = \begin{pmatrix} x_1 \\ x_2 \\ 0 \end{pmatrix}, \qquad
\vec{r} = \vec{v} - P\vec{v} = \begin{pmatrix} 0 \\ 0 \\ x_3 \end{pmatrix}
$$
- Check: $P \cdot P = P$
- The residual is orthogonal to the projection:
$$
\vec{r} \cdot P\vec{v} = \vec{r}^{\,T}(P\vec{v}) = 0
$$
- Any $\vec{v}$ is a linear combination of the basis vectors:
$$
\vec{v} = x_1 \begin{pmatrix} 1 \\ 0 \\ 0 \end{pmatrix} + x_2 \begin{pmatrix} 0 \\ 1 \\ 0 \end{pmatrix} + x_3 \begin{pmatrix} 0 \\ 0 \\ 1 \end{pmatrix}, \qquad
\mathbb{R}^3 = \mathrm{Span}\left\{ \begin{pmatrix} 1 \\ 0 \\ 0 \end{pmatrix}, \begin{pmatrix} 0 \\ 1 \\ 0 \end{pmatrix}, \begin{pmatrix} 0 \\ 0 \\ 1 \end{pmatrix} \right\}
$$
	- Span = all possible linear combinations of the basis

**Least-squares projection (slide correction)**
- The "data space to model space" diagram on the slides is wrong: its 2D plane doesn't properly represent the column space of
$$
A = \begin{pmatrix} 1 & t_1 \\ 1 & t_2 \\ 1 & t_3 \end{pmatrix}
$$

**Noise**
$$
y_i^{\text{data}} = y_i^{\text{truth}} + n_i
$$

**Conditioning vs. stability**
- What is the behavior of a...
	- mathematical problem $\to$ **conditioning**
	- algorithm $\to$ **stability**

**Example: multiplication by 2**
- $f(x) = 2x$, with $f: \mathbb{R} \to \mathbb{R}$
- Perturb the input $x \to x + \delta x$:
$$
f(x + \delta x) = 2(x + \delta x) = 2x + 2\delta x = f(x) + \delta f \quad \Rightarrow \quad \delta f = 2\delta x
$$
- Relative error:
$$
\frac{|\delta f|}{|f|} = \frac{2|\delta x|}{2|x|} = 1 \cdot \frac{|\delta x|}{|x|}
$$
	- Condition number of 1: scaling never amplifies relative error
- Rules of thumb for the condition number:
	- Good: $1$ to $10^4$
	- Eh: $10^4$ to $10^8$
	- Bad: $> 10^8$

**Relative condition number**
- For $f: \mathbb{R}^N \to \mathbb{R}^M$ with input $\vec{x}$ and output $\vec{f}$:
$$
\frac{\|\delta \vec{f}\|}{\|\vec{f}\|} = \kappa(\vec{x}) \, \frac{\|\delta \vec{x}\|_2}{\|\vec{x}\|_2}, \qquad
\kappa = \max_{\vec{x} \in \mathbb{R}^N} \kappa(\vec{x})
$$
	- For the polynomial model the output dimension is technically $M+1$
	- Reminder: $\|\vec{x}\|_2 = \left( \sum_{i=1}^{N} |x_i|^2 \right)^{1/2}$

**Matrix-vector multiplication**
- $f(\vec{x}) = A\vec{x}$, where $A$ is a generic placeholder matrix that could be associated with anything
- Perturb $\vec{x} \to \vec{x} + \delta\vec{x}$:
$$
f(\vec{x} + \delta\vec{x}) = A(\vec{x} + \delta\vec{x}) = A\vec{x} + A\delta\vec{x}
\quad \Rightarrow \quad
\delta\vec{f} = f(\vec{x} + \delta\vec{x}) - f(\vec{x}) = A\delta\vec{x}
$$
- Question: what is $\kappa(\vec{x})$ here?
$$
\frac{\|\delta\vec{f}\|_2}{\|\vec{f}\|_2} = \frac{\|A\delta\vec{x}\|_2}{\|A\vec{x}\|_2} \overset{?}{=} \kappa(\vec{x}) \, \frac{\|\delta\vec{x}\|_2}{\|\vec{x}\|_2}
$$

**Matrix norm**
- For $\vec{y} = A\vec{x}$, the matrix norm is the maximum amplification $\|\vec{y}\|_2 / \|\vec{x}\|_2$
- Example 1: identity
$$
I = \begin{pmatrix} 1 & 0 \\ 0 & 1 \end{pmatrix}, \qquad \vec{y} = I\vec{x} = \vec{x}, \qquad \|I\vec{x}\|_2 = \|\vec{x}\|_2 \quad \Rightarrow \quad \|I\|_2 = 1
$$
- Example 2: diagonal matrix
$$
D = \begin{pmatrix} 4 & 0 \\ 0 & 0.5 \end{pmatrix}, \qquad \vec{x} = \begin{pmatrix} c \\ 0 \end{pmatrix}, \qquad D\vec{x} = \begin{pmatrix} 4c \\ 0 \end{pmatrix} = 4\vec{x} \quad \Rightarrow \quad \|D\|_2 = 4
$$
	- The biggest stretch happens along the direction with the largest diagonal entry
- 2-norm of a matrix $A$:
$$
\|A\|_2 \equiv \max_{\substack{\vec{x} \in \mathbb{R}^N \\ \|\vec{x}\|_2 = 1}} \|A\vec{x}\|_2
\qquad \Rightarrow \qquad
\|A\vec{x}\|_2 \le \|A\|_2 \, \|\vec{x}\|_2
$$
	- Matrix norms in action:
		- ![[Pasted image 20261014165010.png]]

**Condition number of a matrix**
- Bound $\kappa(\vec{x})$ using the matrix norm:
$$
\kappa(\vec{x}) = \left( \frac{\|A\delta\vec{x}\|_2}{\|A\vec{x}\|_2} \right) \left( \frac{\|\vec{x}\|_2}{\|\delta\vec{x}\|_2} \right)
\le \frac{\|A\| \, \|\delta\vec{x}\|}{\|A\vec{x}\|} \cdot \frac{\|\vec{x}\|}{\|\delta\vec{x}\|}
= \|A\| \, \frac{\|\vec{x}\|}{\|A\vec{x}\|}
$$
- Bound the last ratio using $A^{-1}$:
$$
\|\vec{x}\| = \|A^{-1}A\vec{x}\| \le \|A^{-1}\| \, \|A\vec{x}\| \quad \Rightarrow \quad \frac{\|\vec{x}\|}{\|A\vec{x}\|} \le \|A^{-1}\|
$$
- Therefore:
$$
\kappa(\vec{x}) \le \|A\| \, \|A^{-1}\|
$$
- The worst case over all $\vec{x}$ is the conditioning of the matrix:
$$
\kappa(A) = \|A\| \, \|A^{-1}\|
$$
	- $\kappa(\vec{x})$ can be smaller than $\kappa(A)$ for a particular $\vec{x}$

**Pseudoinverse and symmetry of $\kappa$**
- If there is no inverse, use the pseudoinverse $A^+$:
$$
\kappa(A) = \|A\| \, \|A^{-1}\| = \|A^+\| \, \|A\| = \kappa(A^+) = \kappa(A^{-1})
$$
	- $\kappa(A) = \kappa(A^{-1})$ if the inverse exists

**Back to least squares**
- The least-squares solution uses the pseudoinverse:
$$
\vec{w}_* = A^+ \vec{y}
$$
	- For $A$ with independent columns, $A^+ = (A^TA)^{-1}A^T$, which matches $\vec{w}_*$ from Lecture 3
- Perturb the data $\vec{y} \to \vec{y} + \delta\vec{y}$:
$$
\frac{\|\delta\vec{w}_*\|_2}{\|\vec{w}_*\|_2} \le \kappa(A^+) \, \frac{\|\delta\vec{y}\|_2}{\|\vec{y}\|_2}
$$
	- Noisy data gets amplified into the fitted weights by up to $\kappa(A^+)$

## Questions/Gaps/Concerns



## Follow-up 

*actions items to follow-up on (e.g., watch video, re-read notes, hw)*



## References
- Classmate's notes (Lecture 4)
- Slides Day 3: orthogonal projection, least-squares projection, matrix norms in action