2026-10-13 09:00

Course: #eas501 

## Big Ideas

*quick summary of ideas - 3-5 bullet points max*

## Key Concepts

*place links to full notes here*

## Notes

### Summary
- **Cofactor expansion:** expand along *any* row or column.
$$\det A = \sum_k a_{jk}A_{jk}, \qquad A_{jk} = (-1)^{j+k}M_{jk}$$
  $M_{jk}$ is the minor: the determinant left after deleting row $j$ and column $k$. The signs follow a checkerboard: $\begin{pmatrix}+&-&+\\-&+&-\\+&-&+\end{pmatrix}$.
- **Determinants and row operations:**
	- Adding a multiple of one row to another: $\det$ is unchanged.
	- Swapping two rows: $\det$ changes sign.
	- Scaling a row by $\alpha$: $\det$ is multiplied by $\alpha$.
	- Triangular matrix: $\det$ is the product of the diagonal entries.
- **Other determinant rules:**
	- $\det(A^T) = \det A$
	- $\det(AB) = \det A\,\det B$
	- $\det(A+B) \neq \det A + \det B$ in general
- **Rank, in three equivalent forms:**
	- The size of the largest square submatrix with non-zero determinant.
	- The number of LI rows, which equals the number of LI columns (Thm 10.5.2).
	- The number of leading entries in the REF. This is how you compute it in practice.
- **Solution structure (Thm 10.5.3)** for $A\mathbf x = \mathbf c$ with $A$ of size $m\times n$:
	- $\text{rank}(A|\mathbf c) \neq \text{rank}A$: no solution.
	- $\text{rank}(A|\mathbf c) = \text{rank}A = n$: unique solution.
	- $\text{rank}(A|\mathbf c) = \text{rank}A = r < n$: an $(n-r)$-parameter family.
- **General solution:** $\mathbf x = \mathbf x_0 + \alpha_1\mathbf x_1 + \dots + \alpha_p\mathbf x_p$, where $\mathbf x_0$ is one particular solution.
- **Null space:** $\text{span}\{\mathbf x_1,\dots,\mathbf x_p\}$, the solution set of $A\mathbf x = \mathbf 0$.
$$\dim(\text{null space}) = n - \text{rank}A$$
- **Thm 10.5.5:** for square $A$, $A\mathbf x = \mathbf 0$ has a non-trivial solution if and only if $\det A = 0$.

> [!tip] Intuition
> Rank counts how many independent equations you really have. Each one removes one degree of freedom from $n$ unknowns, so $n - r$ freedoms are left. That leftover count is the dimension of the null space. A zero determinant means the columns are squashed into a lower dimension, so some non-zero $\mathbf x$ gets sent to $\mathbf 0$.

> [!warning] Slide typos / notation
> - The determinant definition says "for any fixed $1 \le j \le j$". It should be $1 \le j \le n$.
> - The rank slide lists only two row operations. Scaling a row by $\alpha \neq 0$ is also allowed. It doesn't change the rank, but it multiplies the determinant by $\alpha$.

---
### Worked Examples

Ex 1: Determinant two ways, $A = \begin{pmatrix}1&2&3\\4&5&6\\7&8&10\end{pmatrix}$
- Cofactor expansion along row 1:
$$1(50-48) - 2(40-42) + 3(32-35) = 2 + 4 - 9 = -3$$
- Elimination: $R_2 - 4R_1$ and $R_3 - 7R_1$ give rows $(0,-3,-6)$ and $(0,-6,-11)$. Then $R_3 - 2R_2$ gives $(0,0,1)$.
$$\det A = 1\cdot(-3)\cdot 1 = -3 \checkmark$$

Ex 2: Likely test style — null space basis and rank
- $A = \begin{pmatrix}1&2&1&0\\2&4&3&1\\3&6&4&1\end{pmatrix}$
- $R_2 - 2R_1$ and $R_3 - 3R_1$ both give $(0,0,1,1)$. $R_3 - R_2$ gives $\mathbf 0$. $R_1 - R_2$ gives:
$$\text{RREF} = \begin{pmatrix}1&2&0&-1\\0&0&1&1\\0&0&0&0\end{pmatrix}$$
- The pivots are in columns 1 and 3, so the **free variables are $x_2 = s$ and $x_4 = t$**. Watch out: this pivot pattern is different from the practice exam's.
- $x_1 = -2s + t$ and $x_3 = -t$, so
$$\mathbf x = s\begin{pmatrix}-2\\1\\0\\0\end{pmatrix} + t\begin{pmatrix}1\\0\\-1\\1\end{pmatrix}$$
- $\text{rank}A = 2$ and nullity $= 4 - 2 = 2$ ✓

Ex 3: Reading Thm 10.5.3
- $A$ is $3\times 5$ with rank 2. For some $\mathbf c$, the REF of $(A|\mathbf c)$ has no row of the form $(0\cdots0\,|\,b\neq0)$.
- Then the system is consistent with $5 - 2 = 3$ parameters.

Test Strategy
- Practice Q2 is a null space and rank problem. The student solution is correct.
- Go all the way to **RREF**, and circle the pivots. Every non-pivot column is a free variable.
- Plug each basis vector back in: $A\mathbf x_i = \mathbf 0$.
- State "rank $= r$, nullity $= n - r$" as your final line. It checks itself.
- For a $3\times 3$ determinant, eliminate to triangular form and track any row swaps. Use cofactor expansion if a row or column has zeros.

## Questions/Gaps/Concerns



## Follow-up 

*actions items to follow-up on (e.g., watch video, re-read notes, hw)*



## References

*link to other notes, attachments, or actual lecture slides*
- [[Lec1013_2026.pdf]]
