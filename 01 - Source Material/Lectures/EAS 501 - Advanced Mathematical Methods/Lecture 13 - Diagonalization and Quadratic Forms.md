2026-10-21 09:00

Course: #eas501 

## Big Ideas

*quick summary of ideas - 3-5 bullet points max*

## Key Concepts

*place links to full notes here*

## Notes

### Summary
- **Diagonalization (Thm 11.4.1):** $Q^{-1}AQ = D$ is possible if and only if $A$ has $n$ LI eigenvectors.
	- Put the eigenvectors in as the columns, $Q = (\mathbf e_1\,|\,\cdots\,|\,\mathbf e_n)$.
	- Then $D = \text{diag}(\lambda_1,\dots,\lambda_n)$, **in the same order** as the columns.
- **Sufficient conditions:**
	- $n$ distinct eigenvalues (Thm 11.4.2)
	- $A$ symmetric (Thm 11.4.4)
- **Orthogonal diagonalization** for symmetric $A$:
	- Use **normalized** eigenvectors as the columns of $Q$.
	- For a repeated eigenvalue, first run Gram–Schmidt inside its eigenspace.
	- Then $Q^{-1} = Q^T$, so
$$Q^TAQ = D, \qquad A = QDQ^T$$
- **Quadratic form:** $f(\mathbf x) = \mathbf x^TA\mathbf x$ with $A$ symmetric.
	- Diagonal entry $a_{ii}$ = the coefficient of $x_i^2$.
	- Off-diagonal $a_{ij} = a_{ji}$ = **half** the coefficient of $x_ix_j$.
- **Canonical form:** substitute $\mathbf x = Q\tilde{\mathbf x}$, so $\tilde{\mathbf x} = Q^T\mathbf x$. Then
$$f = \lambda_1\tilde x_1^2 + \dots + \lambda_n\tilde x_n^2$$
- **Positive definite:** all eigenvalues are $> 0$. Then $f(\mathbf x) > 0$ for every $\mathbf x \neq \mathbf 0$.

> [!tip] Intuition
> Diagonalizing means changing coordinates to the eigenvector axes, where $A$ just stretches each axis by its $\lambda$. For a quadratic form, the same rotation removes the cross terms. For example, the tilted ellipse $5x_1^2 + 4x_1x_2 + 2x_2^2 = 1$ becomes an axis-aligned one.

> [!warning] Slide typos / notation
> - The slides say "**model** matrix". The standard term is **modal** matrix.
> - §11.5 is skipped in the slides (it jumps from 11.4 to 11.6). It's worth confirming it isn't on the exam.
> - **Practice exam Q6:** the student solution gave $P$ with *un-normalized* columns. That gives $P^{-1}AP = D$, but the question asks for $Q^TAQ = D$, which needs normalized columns. This is probably where the points were lost (+17). The full answer is in Ex 1 below.

---
### Worked Examples

Ex 1: Complete answer to practice Q6
- $A = \begin{pmatrix}2&1&-1\\1&4&3\\-1&3&4\end{pmatrix}$, with eigenpairs $7 \to (0,1,1)$, $3 \to (-2,-1,1)$, $0 \to (1,-1,1)$
- These are three different eigenvalues, so the eigenvectors are already orthogonal. Normalize them:
$$Q = \begin{pmatrix}0&-\tfrac{2}{\sqrt6}&\tfrac{1}{\sqrt3}\\ \tfrac{1}{\sqrt2}&-\tfrac{1}{\sqrt6}&-\tfrac{1}{\sqrt3}\\ \tfrac{1}{\sqrt2}&\tfrac{1}{\sqrt6}&\tfrac{1}{\sqrt3}\end{pmatrix}, \qquad Q^TAQ = D = \begin{pmatrix}7&0&0\\0&3&0\\0&0&0\end{pmatrix}$$

Ex 2: Likely test style — repeated eigenvalue (the slide matrix)
- $A = \begin{pmatrix}4&2&2\\2&4&2\\2&2&4\end{pmatrix}$ has $\lambda = 8, 2, 2$.
- $\lambda = 8$: $\hat{\mathbf e}_1 = \tfrac{1}{\sqrt3}(1,1,1)$
- $\lambda = 2$: the eigenspace is $x_1 + x_2 + x_3 = 0$. Start from $(-1,1,0)$ and $(-1,0,1)$, then Gram–Schmidt:
$$(-1,0,1) - \tfrac12(-1,1,0) = (-\tfrac12,-\tfrac12,1) \propto (-1,-1,2)$$
- So
$$Q = \begin{pmatrix}\tfrac{1}{\sqrt3}&-\tfrac{1}{\sqrt2}&-\tfrac{1}{\sqrt6}\\ \tfrac{1}{\sqrt3}&\tfrac{1}{\sqrt2}&-\tfrac{1}{\sqrt6}\\ \tfrac{1}{\sqrt3}&0&\tfrac{2}{\sqrt6}\end{pmatrix}, \qquad Q^TAQ = \text{diag}(8,2,2)$$

Ex 3: Quadratic form to canonical form
- $f = 5x_1^2 + 4x_1x_2 + 2x_2^2$, so $A = \begin{pmatrix}5&2\\2&2\end{pmatrix}$. Note the 2, which is half of 4.
$$\lambda^2 - 7\lambda + 6 = (\lambda-6)(\lambda-1)$$
- $\lambda = 6$: $\tfrac{1}{\sqrt5}(2,1)$. $\lambda = 1$: $\tfrac{1}{\sqrt5}(-1,2)$.
$$f = 6\tilde x_1^2 + \tilde x_2^2, \qquad \tilde x_1 = \frac{2x_1 + x_2}{\sqrt5}, \quad \tilde x_2 = \frac{-x_1 + 2x_2}{\sqrt5}$$
- Both eigenvalues are positive, so $f$ is **positive definite**.
- Check by expanding: $\tfrac15\big[6(2x_1+x_2)^2 + (-x_1+2x_2)^2\big] = 5x_1^2 + 4x_1x_2 + 2x_2^2$ ✓

Test Strategy
- "Diagonalize in the form $Q^TAQ = D$" means you must **normalize**. "$Q^{-1}AQ = D$" for a non-symmetric $A$ does not require it.
- Always write out $Q$ **and** $D$, with the column order matching.
- Check: the columns of $Q$ have length 1 and are pairwise orthogonal ($Q^TQ = I$).
- For a repeated eigenvalue, Gram–Schmidt only *within* that eigenspace.

## Questions/Gaps/Concerns



## Follow-up 

*actions items to follow-up on (e.g., watch video, re-read notes, hw)*



## References

*link to other notes, attachments, or actual lecture slides*
- [[Lec1021_2026.pdf]]
