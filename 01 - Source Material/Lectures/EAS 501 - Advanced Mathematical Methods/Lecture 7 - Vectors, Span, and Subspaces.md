2026-09-28 09:00

Course: #eas501 

## Big Ideas

*quick summary of ideas - 3-5 bullet points max*

## Key Concepts

*place links to full notes here*

## Notes

### Summary
- **Dot product, norm, angle** in $\mathbb{R}^n$:
$$\mathbf{u}\cdot\mathbf{v} = \sum_{i=1}^n u_i v_i, \qquad |\mathbf{u}| = \sqrt{\mathbf{u}\cdot\mathbf{u}}, \qquad \theta = \cos^{-1}\!\left(\frac{\mathbf{u}\cdot\mathbf{v}}{|\mathbf{u}|\,|\mathbf{v}|}\right)$$
- **Inequalities:**
	- Schwarz: $|\mathbf{u}\cdot\mathbf{v}| \le |\mathbf{u}|\,|\mathbf{v}|$
	- Triangle: $|\mathbf{u}+\mathbf{v}| \le |\mathbf{u}| + |\mathbf{v}|$
- **Orthogonal:** $\mathbf{u}\cdot\mathbf{v} = 0$. **Orthonormal set:** $\mathbf{u}_i\cdot\mathbf{u}_j = 1$ if $i=j$ and $0$ if $i\neq j$.
- **Vector space:** a set $V$ that is closed under addition and scalar multiplication, contains $\mathbf{0}$, and contains $-\mathbf{u}$ for every $\mathbf{u}$. Examples: $\mathbb{R}^n$, and $M_{2\times 2}$ (2×2 matrices).
- **Inner product axioms:** symmetric, positive ($\mathbf{u}\cdot\mathbf{u} > 0$ for $\mathbf{u}\neq\mathbf{0}$), and linear in each slot.
- **Norm axioms:** $\|\alpha\mathbf{u}\| = |\alpha|\,\|\mathbf{u}\|$, positive for $\mathbf{u}\neq\mathbf{0}$, and the triangle inequality.
- **Span:** all linear combinations
$$\text{span}\{\mathbf{u}_1,\dots,\mathbf{u}_k\} = \{\alpha_1\mathbf{u}_1 + \dots + \alpha_k\mathbf{u}_k\}$$
- **Subspace:** a subset $W \subset V$ that is itself a vector space. Practical test, all three must hold:
	1. $\mathbf{0} \in W$
	2. $\mathbf{u},\mathbf{v} \in W \Rightarrow \mathbf{u}+\mathbf{v} \in W$
	3. $\mathbf{u} \in W \Rightarrow \alpha\mathbf{u} \in W$
- **Theorem 9.7.1:** any span is a subspace.
- **"Is $\text{span}\{\dots\} = \mathbb{R}^n$?"** Ask whether $\alpha_1\mathbf{u}_1 + \dots + \alpha_k\mathbf{u}_k = \mathbf{v}$ is consistent for *every* $\mathbf{v}$. Row reduce with a general right-hand side.

> [!tip] Intuition
> The span of some vectors is everything you can reach by stretching and adding them. Two non-parallel vectors in $\mathbb{R}^3$ span a plane through the origin. Every subspace must pass through the origin, which is why "contains $\mathbf{0}$" is the fastest disqualifier.

> [!warning] Slide typos / notation
> - The inner product and norm slides say "$\mathbf{u}\cdot\mathbf{u} \ge 0$ for any $\mathbf{u}\neq 0$". It should be **strictly** $> 0$. Otherwise the zero-vector condition is meaningless.
> - The vector space slide lists only the addition axioms. The full definition also includes the scalar rules, such as $\alpha(\mathbf{u}+\mathbf{v}) = \alpha\mathbf{u}+\alpha\mathbf{v}$ and $1\cdot\mathbf{u} = \mathbf{u}$.

---
### Worked Examples

Ex 1: Angle between $\mathbf{u} = (1,2,2)$ and $\mathbf{v} = (2,0,1)$
- $\mathbf{u}\cdot\mathbf{v} = 2 + 0 + 2 = 4$, $|\mathbf{u}| = 3$, $|\mathbf{v}| = \sqrt5$
$$\theta = \cos^{-1}\!\left(\frac{4}{3\sqrt5}\right) \approx \cos^{-1}(0.596) \approx 53.4^\circ$$

Ex 2: Is $\text{span}\{(1,2,3),\,(0,1,2),\,(1,3,5)\} = \mathbb{R}^3$?
- Put the vectors in as columns:
$$\det\begin{pmatrix} 1 & 0 & 1 \\ 2 & 1 & 3 \\ 3 & 2 & 5 \end{pmatrix} = 0$$
  So the answer is **no**.
- Reason: $(1,3,5) = (1,2,3) + (0,1,2)$, so the third vector adds nothing.
- The span is the plane through the origin with normal $(1,2,3)\times(0,1,2) = (1,-2,1)$:
$$x - 2y + z = 0$$
  Check $(1,2,3)$: $1 - 4 + 3 = 0$ ✓

Ex 3: Subspace or not?
- $W_1 = \{(x,y,z) : x+y+z = 0\}$: **yes**. It contains $\mathbf 0$, and sums and multiples still satisfy the equation.
- $W_2 = \{(x,y,z) : x+y+z = 1\}$: **no**, because $\mathbf{0}\notin W_2$.
- $W_3 = \{(x,y) : xy \ge 0\}$: **no**. It is closed under scaling, but $(1,0)+(0,-1) = (1,-1)$ has $xy = -1 < 0$.

Test Strategy
- For $n$ vectors in $\mathbb{R}^n$: they span $\mathbb{R}^n$ if and only if $\det \neq 0$. That is the fastest check.
- Fewer than $n$ vectors can **never** span $\mathbb{R}^n$.
- Subspace questions: check $\mathbf{0}$ first. If it passes, prove closure in general, or give one concrete counterexample to disprove.

## Questions/Gaps/Concerns



## Follow-up 

*actions items to follow-up on (e.g., watch video, re-read notes, hw)*



## References

*link to other notes, attachments, or actual lecture slides*
- [[Lec0928_2026.pdf]]
