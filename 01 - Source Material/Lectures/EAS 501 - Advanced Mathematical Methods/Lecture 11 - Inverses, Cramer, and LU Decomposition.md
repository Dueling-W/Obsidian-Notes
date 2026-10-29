2026-10-14 09:00

Course: #eas501 

## Big Ideas

*quick summary of ideas - 3-5 bullet points max*

## Key Concepts

*place links to full notes here*

## Notes

### Summary
- **Inverse:** $A^{-1}A = AA^{-1} = I_n$. It exists if and only if $\det A \neq 0$, and $\det(A^{-1}) = \dfrac{1}{\det A}$.
- **Adjugate formula:**
$$A^{-1} = \frac{1}{\det A}\,\text{adj}A$$
  $\text{adj}A$ is the **transpose** of the cofactor matrix. So the cofactor $A_{21}$ goes in position $(1,2)$.
- **2×2 shortcut:**
$$\begin{pmatrix}a&b\\c&d\end{pmatrix}^{-1} = \frac{1}{ad-bc}\begin{pmatrix}d&-b\\-c&a\end{pmatrix}$$
- **Properties:**
	- $(AB)^{-1} = B^{-1}A^{-1}$
	- $(A^T)^{-1} = (A^{-1})^T$
	- If $A$ is invertible, you can cancel it: $AB = AC \Rightarrow B = C$.
- **Cramer's rule:** for invertible $A$,
$$x_i = \frac{\det A^{(i)}}{\det A}$$
  $A^{(i)}$ is $A$ with column $i$ replaced by $\mathbf c$.
- **Gauss–Jordan:** row reduce $(A\,|\,I)$ until it becomes $(I\,|\,A^{-1})$.
- **LU decomposition** (Doolittle: $l_{ii} = 1$) for a $3\times 3$ matrix:
$$A = LU = \begin{pmatrix}1&0&0\\l_{21}&1&0\\l_{31}&l_{32}&1\end{pmatrix}\begin{pmatrix}u_{11}&u_{12}&u_{13}\\0&u_{22}&u_{23}\\0&0&u_{33}\end{pmatrix}$$
	- Fast method: do Gaussian elimination without row swaps.
	- Each multiplier $l_{ij}$ = (entry being eliminated) ÷ (pivot) goes into $L$ at position $(i,j)$.
	- $U$ is the final echelon matrix.
- **Solving with LU:** $L\mathbf y = \mathbf c$ by forward substitution, then $U\mathbf x = \mathbf y$ by back substitution.

> [!tip] Intuition
> $L$ is a record of the elimination steps, and $U$ is the result. Once you have both, every new right-hand side costs two cheap triangular solves instead of a full elimination. Gauss–Jordan on $(A\,|\,I)$ solves $n$ systems at once, one for each column of $I$, and the answers are the columns of $A^{-1}$.

> [!warning] Slide typos / notation
> - "Any square matrix has an LU decomposition" is **not true in general**. It fails if a zero pivot appears, for example $\begin{pmatrix}0&1\\1&0\end{pmatrix}$. Then you need a row swap, $PA = LU$. Exam matrices will be chosen so that it works.
> - Remember that the adjugate is the transpose of the cofactor matrix. Forgetting the transpose is the most common error with that formula.

---
### Worked Examples

Ex 1: Likely test style — Gauss–Jordan inverse of $A = \begin{pmatrix}1&2&0\\0&1&1\\1&0&2\end{pmatrix}$
- $R_3 - R_1$:
$$\left(\begin{array}{ccc|ccc} 1&2&0&1&0&0 \\ 0&1&1&0&1&0 \\ 0&-2&2&-1&0&1 \end{array}\right)$$
- $R_3 + 2R_2$, then $\tfrac14 R_3$: the third row becomes $(0,0,1\,|\,-\tfrac14,\tfrac12,\tfrac14)$.
- $R_2 - R_3$: the second row becomes $(0,1,0\,|\,\tfrac14,\tfrac12,-\tfrac14)$.
- $R_1 - 2R_2$: the first row becomes $(1,0,0\,|\,\tfrac12,-1,\tfrac12)$.
$$A^{-1} = \begin{pmatrix}\tfrac12&-1&\tfrac12\\ \tfrac14&\tfrac12&-\tfrac14\\ -\tfrac14&\tfrac12&\tfrac14\end{pmatrix}, \qquad \det A = 4$$
- Check row 1 of $A$ times column 1 of $A^{-1}$: $\tfrac12 + 2\cdot\tfrac14 + 0 = 1$ ✓

Ex 2: Likely test style — LU, then solve
- $A = \begin{pmatrix}2&1&1\\4&3&3\\8&7&9\end{pmatrix}$ and $\mathbf c = (4,10,24)^T$
- $l_{21} = 4/2 = 2$ and $l_{31} = 8/2 = 4$. The new rows are $(0,1,1)$ and $(0,3,5)$.
- $l_{32} = 3/1 = 3$. The new last row is $(0,0,2)$.
$$L = \begin{pmatrix}1&0&0\\2&1&0\\4&3&1\end{pmatrix}, \qquad U = \begin{pmatrix}2&1&1\\0&1&1\\0&0&2\end{pmatrix}$$
- Forward substitution, $L\mathbf y = \mathbf c$: $\mathbf y = (4,\,10-8,\,24-16-6) = (4,2,2)$
- Back substitution, $U\mathbf x = \mathbf y$: $\mathbf x = (1,1,1)$
- Check: $2+1+1 = 4$ ✓

Ex 3: Finishing the slide's Cramer example
- The slide stops at $x_2$. For $x_3$, replace column 3 with $\mathbf c$:
$$\det A^{(3)} = \begin{vmatrix}1&3&5\\-2&3&1\\0&1&-2\end{vmatrix} = 1(-7) - 3(4) + 5(-2) = -29$$
$$x_3 = -\frac{29}{8}$$

Test Strategy
- Practice Q3 (LU) and Q4 (4×4 inverse) are both correct in the student solution. I checked the 4×4 inverse:
$$A^{-1} = \begin{pmatrix}13&-2&4&-4\\-\tfrac{29}{4}&\tfrac54&-\tfrac94&\tfrac52\\-\tfrac54&\tfrac14&-\tfrac14&\tfrac12\\-\tfrac{13}{8}&\tfrac18&-\tfrac58&\tfrac34\end{pmatrix}$$
- For LU, multiply at least the last row of $L$ by $U$ to confirm you get back row 3 of $A$.
- For an inverse, check one row of $AA^{-1}$.
- A 4×4 Gauss–Jordan takes 20+ minutes. If your calculator has a matrix mode, use it to *check* the final answer, not to replace the work.
- Don't swap rows during LU. Do swap rows freely during Gauss–Jordan.

## Questions/Gaps/Concerns



## Follow-up 

*actions items to follow-up on (e.g., watch video, re-read notes, hw)*



## References

*link to other notes, attachments, or actual lecture slides*
- [[Lec1014_2026.pdf]]
