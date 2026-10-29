2026-10-19 09:00

Course: #eas501 

## Big Ideas

*quick summary of ideas - 3-5 bullet points max*

## Key Concepts

*place links to full notes here*

## Notes

### Summary
- **Definition:** $A\mathbf x = \lambda\mathbf x$ with $\mathbf x \neq \mathbf 0$. Equivalently, $(A-\lambda I)\mathbf x = \mathbf 0$ has a non-trivial solution.
- **Characteristic equation:**
$$\det(\lambda I_n - A) = 0$$
  This is a degree-$n$ polynomial with leading coefficient 1, so there are at most $n$ eigenvalues.
- **Eigenvectors:** for each $\lambda$, the eigenvectors are the null space of $A - \lambda I$. Any non-zero multiple is also an eigenvector.
- **Free sanity checks:**
	- $\lambda_1 + \dots + \lambda_n = \text{tr}A$ (the sum of the diagonal)
	- $\lambda_1\cdots\lambda_n = \det A$
	- $\lambda = 0$ is an eigenvalue if and only if $A$ is singular.
	- For a triangular matrix, the eigenvalues are the diagonal entries.
- **Symmetric matrices ($A^T = A$):**
	- 11.3.1: all eigenvalues are real.
	- 11.3.2: an eigenvalue of multiplicity $k$ has a $k$-dimensional eigenspace, so you never run short of eigenvectors.
	- 11.3.3: eigenvectors for **different** eigenvalues are orthogonal.
	- 11.3.4: the eigenvectors give an orthogonal basis of $\mathbb{R}^n$.
- **Speed trick for 3×3 matrices:** when $\lambda$ is a simple root, the eigenvector is orthogonal to every row of $A - \lambda I$. So it is the **cross product of any two non-parallel rows**.

> [!tip] Intuition
> An eigenvector is a direction that $A$ only stretches and never turns. $\lambda$ is the stretch factor. A symmetric matrix stretches along perpendicular axes, like a perfect ellipse, which is why its eigenvectors come out orthogonal.

> [!warning] Slide typos / notation
> - In Ex 11.3 #1(e), the two eigenvectors given for $\lambda = 2$, $(-1,1,0)$ and $(-1,0,1)$, are **not** orthogonal to each other: their dot product is 1. Thm 11.3.3 only guarantees orthogonality *between different* eigenvalues. For orthogonal diagonalization you must run Gram–Schmidt inside the repeated eigenspace. See [[Lecture 13 - Diagonalization and Quadratic Forms]].
> - The slides use $\det(\lambda I - A)$, while some books use $\det(A - \lambda I)$. They differ by a factor of $(-1)^n$ and have the same roots.

---
### Worked Examples

Ex 1: A 2×2 warm-up, $A = \begin{pmatrix}4&1\\2&3\end{pmatrix}$
$$\lambda^2 - 7\lambda + 10 = (\lambda-2)(\lambda-5)$$
- Check: $\text{tr} = 7$ and $\det = 10$ ✓
- $\lambda = 5$: $\mathbf x = (1,1)$
- $\lambda = 2$: $\mathbf x = (-1,2)$. Check: $A(-1,2)^T = (-2,4)^T = 2(-1,2)^T$ ✓

Ex 2: Not enough eigenvectors, $A = \begin{pmatrix}2&1\\0&2\end{pmatrix}$
- $\lambda = 2$ is a double root, but $A - 2I = \begin{pmatrix}0&1\\0&0\end{pmatrix}$ gives only $\mathbf x = (1,0)$.
- There is only one independent eigenvector, so this matrix is **not diagonalizable**. A symmetric matrix can never do this (Thm 11.3.2).

Ex 3: Cross-product trick on practice Q6, $\lambda = 7$
- The first two rows of $A - 7I$ are $(-5,1,-1)$ and $(1,-3,3)$.
$$(-5,1,-1)\times(1,-3,3) = (0,14,14) \propto (0,1,1) \checkmark$$

Test Strategy
- Practice Q5 is correct: $\lambda = -2, 2, 0$ with eigenvectors $(-2,1,0)$, $(2,3,4)$ (written there as $(\tfrac12,\tfrac34,1)$), and $(-2,1,2)$ (written as $(-1,\tfrac12,1)$).
- When expanding $\det(\lambda I - A)$, expand along the row or column with the most zeros. Then factor by testing integer roots that divide the constant term.
- **Check trace and determinant before finding eigenvectors.** On practice Q6, the rough work first gave $4, 3, 0$, but $4 + 3 + 0 \neq 10 = \text{tr}A$. This check catches that in seconds.
- Verify each eigenvector with one multiplication: $A\mathbf v = \lambda\mathbf v$.

## Questions/Gaps/Concerns



## Follow-up 

*actions items to follow-up on (e.g., watch video, re-read notes, hw)*



## References

*link to other notes, attachments, or actual lecture slides*
- [[Lec1019_2026.pdf]]
