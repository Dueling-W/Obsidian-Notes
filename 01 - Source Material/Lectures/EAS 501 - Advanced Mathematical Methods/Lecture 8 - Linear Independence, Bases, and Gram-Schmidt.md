2026-10-05 09:00

Course: #eas501 

## Big Ideas

*quick summary of ideas - 3-5 bullet points max*

## Key Concepts

*place links to full notes here*

## Notes

### Summary
- **Linear dependence (LD):** some vector in the set is a combination of the others. Otherwise the set is **linearly independent (LI)**.
- **Test (Thm 9.8.1):** solve
$$\alpha_1\mathbf{u}_1 + \dots + \alpha_k\mathbf{u}_k = \mathbf{0}$$
	- Only the trivial solution means LI.
	- A non-trivial solution means LD.
- **Shortcuts:**
	- $n$ vectors in $\mathbb{R}^n$: LI if and only if $\det \neq 0$.
	- More than $n$ vectors in $\mathbb{R}^n$: always LD.
	- Any set containing $\mathbf{0}$: LD (Thm 9.8.3).
	- Two vectors: LD if and only if one is a multiple of the other (Thm 9.8.2).
	- Orthogonal non-zero vectors: always LI (Thm 9.8.5).
- **Basis:** a set that is LI **and** spans $V$. Then every $\mathbf u$ has a *unique* expansion in it.
- **Dimension:** $\dim V$ is the number of vectors in any basis. For example, $\dim\mathbb{R}^n = n$.
- **Expansion in an orthogonal basis** (no system to solve):
$$\mathbf{u} = \sum_j \frac{\mathbf{u}\cdot\mathbf{e}_j}{|\mathbf{e}_j|^2}\,\mathbf{e}_j = \sum_j (\mathbf{u}\cdot\hat{\mathbf{e}}_j)\,\hat{\mathbf{e}}_j$$
- **Gram–Schmidt** turns $\{\mathbf v_1,\dots,\mathbf v_k\}$ into an orthonormal set with the same span:
$$\mathbf e_1 = \mathbf v_1, \qquad \mathbf e_j = \mathbf v_j - \sum_{i=1}^{j-1}(\mathbf v_j\cdot\hat{\mathbf e}_i)\,\hat{\mathbf e}_i, \qquad \hat{\mathbf e}_j = \frac{\mathbf e_j}{|\mathbf e_j|}$$

> [!tip] Intuition
> Gram–Schmidt removes from each new vector its shadow on the directions you already have. Whatever is left is perpendicular to all of them. Only the *direction* of $\mathbf e_j$ matters before normalizing, so you can scale it to clear fractions. $(\tfrac12, -\tfrac12, 1)$ and $(1,-1,2)$ normalize to the same $\hat{\mathbf e}_j$.

> [!warning] Slide typos / notation
> - **Thm 9.9.1** as written says "basis iff span $= V$". It is missing the condition that the set must also be **linearly independent**.
> - "$\dim(\text{span}\{\mathbf u_1,\dots,\mathbf u_k\}) = k$" is only true when the $\mathbf u_i$ are LI.
> - Ex 9.8 #3(b) argues "the system is consistent, so the vectors are LD". Every homogeneous system is consistent, since $\mathbf 0$ always works. The real reason is that there are 4 unknowns and only 2 equations, so there are free variables and a non-trivial solution exists.
> - **Notation clash:** the slides use $\mathbf e_j$ (un-normalized) and $\hat{\mathbf e}_j$ (normalized). The practice exam solution used $\mathbf u_k$ and $\mathbf e_k$. Pick one convention and label it on the exam.

---
### Worked Examples

Ex 1: LI test for $(1,1,0),\ (1,0,1),\ (0,1,1)$
$$\det\begin{pmatrix} 1 & 1 & 0 \\ 1 & 0 & 1 \\ 0 & 1 & 1 \end{pmatrix} = -2 \neq 0$$
- So the set is LI, and it is a basis of $\mathbb{R}^3$.

Ex 2: Likely test style — Gram–Schmidt on the same three vectors
- $\hat{\mathbf e}_1 = \tfrac{1}{\sqrt2}(1,1,0)$
- $\mathbf v_2\cdot\hat{\mathbf e}_1 = \tfrac{1}{\sqrt2}$, so
$$\mathbf e_2 = (1,0,1) - \tfrac12(1,1,0) = (\tfrac12,-\tfrac12,1) \propto (1,-1,2), \qquad \hat{\mathbf e}_2 = \tfrac{1}{\sqrt6}(1,-1,2)$$
- $\mathbf v_3\cdot\hat{\mathbf e}_1 = \tfrac{1}{\sqrt2}$ and $\mathbf v_3\cdot\hat{\mathbf e}_2 = \tfrac{1}{\sqrt6}$, so
$$\mathbf e_3 = (0,1,1) - \tfrac12(1,1,0) - \tfrac16(1,-1,2) = (-\tfrac23,\tfrac23,\tfrac23), \qquad \hat{\mathbf e}_3 = \tfrac{1}{\sqrt3}(-1,1,1)$$
- Check: all three pairwise dot products are 0 ✓

Ex 3: Expansion in an orthogonal basis
- Write $\mathbf u = (3,1,2)$ in the basis $(1,1,0),\ (1,-1,2),\ (-1,1,1)$:
$$\frac{\mathbf u\cdot\mathbf e_1}{|\mathbf e_1|^2} = \frac42 = 2, \qquad \frac{\mathbf u\cdot\mathbf e_2}{|\mathbf e_2|^2} = \frac66 = 1, \qquad \frac{\mathbf u\cdot\mathbf e_3}{|\mathbf e_3|^2} = \frac03 = 0$$
- So $\mathbf u = 2(1,1,0) + 1(1,-1,2) = (3,1,2)$ ✓

Test Strategy
- Practice Q1 is a Gram–Schmidt problem. The student solution there is fully correct, decimals included. Use it as an answer key.
- Write the formula first, then compute. Keep exact radicals, since that is how the professor writes answers. Use calculator decimals only as a check.
- Final check: $\hat{\mathbf e}_i\cdot\hat{\mathbf e}_j = 0$ for $i \neq j$, and each $|\hat{\mathbf e}_j| = 1$.
- Budget about 15 minutes for three vectors in $\mathbb{R}^3$.

## Questions/Gaps/Concerns



## Follow-up 

*actions items to follow-up on (e.g., watch video, re-read notes, hw)*



## References

*link to other notes, attachments, or actual lecture slides*
- [[Lec1005_2026.pdf]]
