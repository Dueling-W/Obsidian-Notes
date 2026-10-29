2026-10-07 09:00

Course: #eas501 

## Big Ideas

*quick summary of ideas - 3-5 bullet points max*

## Key Concepts

*place links to full notes here*

## Notes

### Summary
- **Best approximation (Thm 9.10.1):** let $\{\hat{\mathbf e}_1,\dots,\hat{\mathbf e}_N\}$ be **orthonormal** with $N < \dim V$. The closest point to $\mathbf u$ in their span is
$$\mathbf u_N = \sum_{j=1}^N (\mathbf u\cdot\hat{\mathbf e}_j)\,\hat{\mathbf e}_j, \qquad \mathbf E = \mathbf u - \mathbf u_N$$
  This choice makes $|\mathbf E|$ as small as possible, and $\mathbf E$ is orthogonal to every $\hat{\mathbf e}_j$.
- **Matrix algebra:**
	- $(A+B)_{ij} = a_{ij}+b_{ij}$ and $(\alpha A)_{ij} = \alpha a_{ij}$
	- $(AB)_{ij} = \sum_k a_{ik}b_{kj}$, which needs $(m\times n)(n\times p) = m\times p$
	- $AI_n = A$ and $I_nB = B$
- **Things that fail for matrices:**
	- $AB \ne BA$ in general.
	- $AB = AC$ does not imply $B = C$.
	- $AB = 0$ does not imply $A = 0$ or $B = 0$.
	- $A^2 = I$ does not imply $A = \pm I$.
- **Expansions need commuting matrices:** $(A+B)^2 = A^2 + AB + BA + B^2$. This equals $A^2 + 2AB + B^2$ **only if** $AB = BA$.
- **Transpose:** $(A^T)_{ij} = a_{ji}$. Rules: $(A^T)^T = A$, $(A+B)^T = A^T+B^T$, and $(AB)^T = B^TA^T$ (the "putting on, taking off" principle).
- **Symmetric:** $A^T = A$. **Skew-symmetric:** $A^T = -A$.

> [!tip] Intuition
> The best approximation is the shadow of $\mathbf u$ on the subspace, cast straight down. The error $\mathbf E$ is the vertical drop, so it is perpendicular to the subspace. Any other point in the subspace is the hypotenuse of a right triangle, which makes it farther away.

> [!warning] Slide typos / notation
> - The title slide is dated **10/07/2027**. It should be 2026.
> - In Ex 10.2 #8(c), the product for $C^2$ is garbled ("0 30 0"). It means $\begin{pmatrix}0&3\\0&0\end{pmatrix}\begin{pmatrix}0&3\\0&0\end{pmatrix}$.
> - Thm 9.10.1 needs **orthonormal** $\hat{\mathbf e}_j$. If you are given an orthogonal but not normalized set, use $\dfrac{\mathbf u\cdot\mathbf e_j}{|\mathbf e_j|^2}\mathbf e_j$. If the set is not orthogonal at all, run Gram–Schmidt first.

---
### Worked Examples

Ex 1: Likely test style — best approximation and error
- $\mathbf u = (1,2,3)$, $\hat{\mathbf e}_1 = (1,0,0)$, $\hat{\mathbf e}_2 = \tfrac{1}{\sqrt2}(0,1,1)$
- $\mathbf u\cdot\hat{\mathbf e}_1 = 1$ and $\mathbf u\cdot\hat{\mathbf e}_2 = \tfrac{5}{\sqrt2}$
$$\mathbf u_N = 1\cdot(1,0,0) + \tfrac52(0,1,1) = (1,\tfrac52,\tfrac52)$$
$$\mathbf E = (0,-\tfrac12,\tfrac12), \qquad |\mathbf E| = \tfrac{\sqrt2}{2}$$
- Check: $\mathbf E\cdot\hat{\mathbf e}_1 = 0$ and $\mathbf E\cdot\hat{\mathbf e}_2 = 0$ ✓

Ex 2: Matrix powers
- $A = \begin{pmatrix}1&1\\1&1\end{pmatrix}$. Then $A^2 = 2A$, so by induction $A^n = 2^{n-1}A$.
$$A^5 = 16A = \begin{pmatrix}16&16\\16&16\end{pmatrix}$$

Ex 3: Short proof — $A^TA$ is always symmetric
$$(A^TA)^T = A^T(A^T)^T = A^TA$$

Test Strategy
- Report $\mathbf u_N$, $\mathbf E$, and $|\mathbf E|$. "How good is the approximation" means $|\mathbf E|$.
- Check that $\mathbf E\cdot\hat{\mathbf e}_j = 0$ for every $j$. If it isn't, you made an arithmetic error.
- For a "true or false" matrix identity, expand it and see whether it needs $AB = BA$.

## Questions/Gaps/Concerns



## Follow-up 

*actions items to follow-up on (e.g., watch video, re-read notes, hw)*



## References

*link to other notes, attachments, or actual lecture slides*
- [[Lec1007_2026.pdf]]
