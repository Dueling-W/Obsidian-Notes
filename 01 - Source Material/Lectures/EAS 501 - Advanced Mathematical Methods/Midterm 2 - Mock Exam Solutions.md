Course: #eas501 

# Midterm 2 Mock Exam — Solutions

> [!warning] Don't open until you've finished the timed attempt
> Grade yourself generously on method and strictly on final answers. That seems close to how the professor grades.

---

### 1. Gram–Schmidt + best approximation
**(a)**
- $\hat{\mathbf e}_1 = \tfrac{1}{\sqrt2}(1,0,1)$
- $\mathbf v_2\cdot\hat{\mathbf e}_1 = \tfrac{2}{\sqrt2}$, so
$$\mathbf e_2 = (2,1,0) - (1,0,1) = (1,1,-1), \qquad \hat{\mathbf e}_2 = \tfrac{1}{\sqrt3}(1,1,-1)$$
- $\mathbf v_3\cdot\hat{\mathbf e}_1 = \tfrac{2}{\sqrt2}$ and $\mathbf v_3\cdot\hat{\mathbf e}_2 = \tfrac{1}{\sqrt3}$, so
$$\mathbf e_3 = (1,1,1) - (1,0,1) - \tfrac13(1,1,-1) = (-\tfrac13,\tfrac23,\tfrac13), \qquad \hat{\mathbf e}_3 = \tfrac{1}{\sqrt6}(-1,2,1)$$

**(b)**
- $\mathbf u\cdot\hat{\mathbf e}_1 = \tfrac{5}{\sqrt2}$ and $\mathbf u\cdot\hat{\mathbf e}_2 = \tfrac{2}{\sqrt3}$
$$\mathbf u_N = \tfrac52(1,0,1) + \tfrac23(1,1,-1) = \left(\tfrac{19}{6},\tfrac23,\tfrac{11}{6}\right)$$
$$\mathbf E = \mathbf u - \mathbf u_N = \left(-\tfrac16,\tfrac13,\tfrac16\right), \qquad |\mathbf E| = \tfrac{\sqrt6}{6} \approx 0.408$$
- Check: $\mathbf E = \tfrac16(-1,2,1)$, which points along $\hat{\mathbf e}_3$. That makes sense, since the error is the part of $\mathbf u$ outside the plane.

### 2. Null space, rank, consistency
**(a)** Row reduce:
- $R_2 - 2R_1$ and $R_3 - R_1$ both give $(0,0,1,1,1)$.
- $R_3 - R_2$ gives $\mathbf 0$.
- $R_1 - 2R_2$ gives:
$$\text{RREF} = \begin{pmatrix}1&-1&0&-2&-1\\0&0&1&1&1\\0&0&0&0&0\end{pmatrix}$$
- The pivots are in columns 1 and 3. The free variables are $x_2 = s$, $x_4 = t$, $x_5 = w$.
- Then $x_1 = s + 2t + w$ and $x_3 = -t - w$, so the null space basis is
$$\begin{pmatrix}1\\1\\0\\0\\0\end{pmatrix}, \quad \begin{pmatrix}2\\0\\-1\\1\\0\end{pmatrix}, \quad \begin{pmatrix}1\\0\\-1\\0\\1\end{pmatrix}$$
- **Rank 2**, nullity 3, and $2 + 3 = 5$ ✓

**(b)**
- Carry the right-hand side through the same row operations. The last row becomes $(0\cdots0\,|\,k-2)$.
- So the system is consistent **iff $k = 2$**. Then there are $5 - 2 = 3$ parameters.
- A particular solution is $\mathbf x_0 = (-1,0,1,0,0)^T$. Check: rows give $1$, $3$, $2$ ✓

**(c)** No. The rank is $2 < 5$ columns. Also, 5 vectors in $\mathbb{R}^3$ are always dependent.

### 3. LU
- $l_{21} = 2$ and $l_{31} = -1$. The new rows are $(0,-3,3)$ and $(0,6,1)$.
- $l_{32} = 6/(-3) = -2$. The new last row is $(0,0,1 + 6) = (0,0,7)$.
$$L = \begin{pmatrix}1&0&0\\2&1&0\\-1&-2&1\end{pmatrix}, \qquad U = \begin{pmatrix}1&2&-1\\0&-3&3\\0&0&7\end{pmatrix}$$
- Forward substitution, $L\mathbf y = \mathbf c$: $y_1 = -3$, $y_2 = 3 + 6 = 9$, $y_3 = -1 - 3 + 18 = 14$
- Back substitution, $U\mathbf x = \mathbf y$: $x_3 = 14/7 = 2$, $x_2 = \frac{9 - 3(2)}{-3} = -1$, $x_1 = -3 - 2x_2 + x_3 = -3 + 2 + 2 = 1$
$$\mathbf x = (1,-1,2)^T$$
- **Common trap:** the sign of $l_{32}$. The multiplier is (entry being eliminated) ÷ (pivot) $= 6 \div (-3)$.

### 4. Inverse, solve, Cramer
**(a)** One clean path:
- Swap $R_1$ and $R_2$.
- $R_2 - 2R_1$, then $R_3 + R_2$, then $-R_2$.
- $R_2 - 2R_3$, then $R_1 - R_3$, then $R_1 - R_2$.
$$A^{-1} = \begin{pmatrix}2&-3&1\\-3&6&-2\\1&-2&1\end{pmatrix}, \qquad \det A = 2(3-1) - 1(3-0) = 1$$

**(b)**
$$\mathbf x = A^{-1}(1,2,3)^T = (2-6+3,\ -3+12-6,\ 1-4+3)^T = (-1,3,0)^T$$

**(c)**
$$\det A^{(2)} = \begin{vmatrix}2&1&0\\1&2&1\\0&3&3\end{vmatrix} = 2(6-3) - 1(3-0) = 3, \qquad x_2 = \frac31 = 3 \checkmark$$

### 5. Non-symmetric diagonalization
**(a)** Expand $\det(\lambda I - A)$ along column 2:
$$(\lambda - 1)\big[(\lambda-4)(\lambda-1) + 2\big] = (\lambda-1)(\lambda-2)(\lambda-3)$$
- Check: trace $= 6 = 1+2+3$ and $\det A = 6 = 1\cdot2\cdot3$ ✓
- $\lambda = 1$: $(0,1,0)$
- $\lambda = 2$: $(-1,2,2)$
- $\lambda = 3$: $(-1,1,1)$

**(b)**
$$Q = \begin{pmatrix}0&-1&-1\\1&2&1\\0&2&1\end{pmatrix}, \qquad D = \text{diag}(1,2,3)$$

**(c)** No. $A$ is not symmetric, and its eigenvectors are not orthogonal. For example, $(-1,2,2)\cdot(-1,1,1) = 5 \neq 0$. An orthogonal $Q$ only exists for symmetric $A$.

### 6. Orthogonal diagonalization + quadratic form
**(a)**
- Each row of $A$ sums to 0, so $A(1,1,1)^T = \mathbf 0$. That gives $\lambda = 0$.
- $A - 3I$ has every entry equal to $-1$, so it has rank 1. That makes $\lambda = 3$ a double eigenvalue, and the trace $6 = 0 + 3 + 3$ ✓.
- Full characteristic polynomial: $\lambda(\lambda-3)^2$.
- $\lambda = 0$: $\hat{\mathbf e}_1 = \tfrac{1}{\sqrt3}(1,1,1)$
- $\lambda = 3$: the eigenspace is $x_1 + x_2 + x_3 = 0$. Start from $(1,-1,0)$ and $(1,0,-1)$, then Gram–Schmidt:
$$(1,0,-1) - \tfrac12(1,-1,0) = (\tfrac12,\tfrac12,-1) \propto (1,1,-2)$$
$$Q = \begin{pmatrix}\tfrac{1}{\sqrt3}&\tfrac{1}{\sqrt2}&\tfrac{1}{\sqrt6}\\ \tfrac{1}{\sqrt3}&-\tfrac{1}{\sqrt2}&\tfrac{1}{\sqrt6}\\ \tfrac{1}{\sqrt3}&0&-\tfrac{2}{\sqrt6}\end{pmatrix}, \qquad Q^TAQ = D = \begin{pmatrix}0&0&0\\0&3&0\\0&0&3\end{pmatrix}$$

**(b)**
- $f = \mathbf x^TA\mathbf x$, since each off-diagonal entry is $-1$, half of $-2$. With $\mathbf x = Q\tilde{\mathbf x}$:
$$f = 0\cdot\tilde x_1^2 + 3\tilde x_2^2 + 3\tilde x_3^2$$
- It is **not positive definite**, because one eigenvalue is 0. For example, $f(1,1,1) = 0$ with $\mathbf x \neq \mathbf 0$. (It is positive *semi*-definite.)

---

### Rough grading guide (per problem, 25 pts)
- **~10 pts** for correct setup and method: formula written, row operations labeled, characteristic polynomial set up.
- **~10 pts** for correct intermediate results.
- **~5 pts** for the final answer in the requested form: normalized $Q$, both $L$ and $U$, rank stated.
