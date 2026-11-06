### FRONT: Systems, Spaces, Rank (Lec 6–10)

**Row reduction.** Allowed ops: scale a row by $\alpha\neq0$, add $\alpha R_j$ to $R_i$, swap two rows. Label each one ($R_2-2R_1$). **REF:** zeros below each pivot. **RREF:** pivots are 1, with zeros above and below.
- A row $(0\cdots0\,|\,b\neq0)$ means **no solution**. Free variables are the non-pivot columns, and #parameters $= n-\#\text{pivots}$.
- **Thm 10.5.3** ($r=\text{rank}A$, $n$ unknowns): $\text{rank}(A|\mathbf c)\neq r$ gives none, $=r=n$ gives unique, $=r<n$ gives an $(n-r)$-parameter family. General solution: $\mathbf x=\mathbf x_0+\alpha_1\mathbf x_1+\dots+\alpha_p\mathbf x_p$.

**Null space & rank.** (1) Row reduce; use RREF if there are 2+ free variables. Circle the pivots. (2) Set the free variables to $s,t,\dots$ and solve for the pivot variables. (3) $\mathbf x=s\mathbf x_1+t\mathbf x_2+\cdots$, and the $\mathbf x_i$ are the basis. (4) **Check** $A\mathbf x_i=\mathbf 0$, rank $=$ #pivots, and rank + nullity $=n$.
- Rank $=$ #LI rows $=$ #LI columns $\le\min(m,n)$. Square $A$: a non-trivial solution of $A\mathbf x=\mathbf 0$ exists $\iff\det A=0$.

**Vectors.** $\mathbf u\cdot\mathbf v=\sum u_iv_i$, $|\mathbf u|=\sqrt{\mathbf u\cdot\mathbf u}$, $\cos\theta=\frac{\mathbf u\cdot\mathbf v}{|\mathbf u||\mathbf v|}$, $|\mathbf u\cdot\mathbf v|\le|\mathbf u||\mathbf v|$. Cross product: $\mathbf a\times\mathbf b=(a_2b_3-a_3b_2,\ a_3b_1-a_1b_3,\ a_1b_2-a_2b_1)$.

**Subspace test:** (1) $\mathbf 0\in W$ (check first), (2) closed under $+$, (3) closed under scalar multiples. One counterexample disproves. Any span is a subspace. $n$ vectors span $\mathbb R^n\iff\det\neq0$, and fewer than $n$ vectors never span $\mathbb R^n$.

**LI & bases.** LI $\iff\sum\alpha_i\mathbf u_i=\mathbf 0$ only for all $\alpha_i=0$.
- Shortcuts: $n$ vectors in $\mathbb R^n$ are LI $\iff\det\neq0$. More than $n$ vectors is LD. A set containing $\mathbf 0$ is LD. Orthogonal non-zero vectors are LI.
- **Basis** = LI **and** spans. $\dim$ = #basis vectors. Orthogonal expansion: $\mathbf u=\sum_j\frac{\mathbf u\cdot\mathbf e_j}{|\mathbf e_j|^2}\mathbf e_j$.

**Gram–Schmidt** (normalize only at the end):
$$\mathbf e_1=\mathbf v_1,\quad \mathbf e_2=\mathbf v_2-\tfrac{\mathbf v_2\cdot\mathbf e_1}{|\mathbf e_1|^2}\mathbf e_1,\quad \mathbf e_3=\mathbf v_3-\tfrac{\mathbf v_3\cdot\mathbf e_1}{|\mathbf e_1|^2}\mathbf e_1-\tfrac{\mathbf v_3\cdot\mathbf e_2}{|\mathbf e_2|^2}\mathbf e_2,\quad \hat{\mathbf e}_j=\tfrac{\mathbf e_j}{|\mathbf e_j|}$$
- Scale each $\mathbf e_j$ to clear fractions first: $(\tfrac43,-\tfrac53,\tfrac13)\to(4,-5,1)$. That way there is no rounding.
- **Check** $\hat{\mathbf e}_i\cdot\hat{\mathbf e}_j=0$ and $|\hat{\mathbf e}_j|=1$. Box the exact radicals, and write $\approx$ for decimals.

**Best approximation** (orthonormal $\hat{\mathbf e}_j$): $\mathbf u_N=\sum_j(\mathbf u\cdot\hat{\mathbf e}_j)\hat{\mathbf e}_j$, $\mathbf E=\mathbf u-\mathbf u_N$. Report $|\mathbf E|$, and check $\mathbf E\cdot\hat{\mathbf e}_j=0$. If the set isn't orthonormal, run Gram–Schmidt first.

**Matrix algebra.** $(m\times n)(n\times p)=m\times p$. $AB\neq BA$ in general. $AB=0$ does not imply $A=0$ or $B=0$. $(A+B)^2=A^2+2AB+B^2$ **only if** $AB=BA$. $(AB)^T=B^TA^T$. $A^TA$ is symmetric. Skew-symmetric means $A^T=-A$.

**Determinants.** Cofactor expansion along any row or column: $\det A=\sum_k a_{jk}(-1)^{j+k}M_{jk}$. Signs $\left(\begin{smallmatrix}+&-&+\\-&+&-\\+&-&+\end{smallmatrix}\right)$. Pick the row or column with the most zeros.
- $3\times3$: $a(ei-fh)-b(di-fg)+c(dh-eg)$. Triangular: product of the diagonal.
- Row ops: adding a multiple leaves $\det$ unchanged, a swap flips the sign, scaling by $\alpha$ multiplies by $\alpha$.
- $\det A^T=\det A$, $\det AB=\det A\det B$, $\det A^{-1}=1/\det A$, and $\det(A+B)\neq\det A+\det B$.

<div style="page-break-after: always;"></div>

### BACK: Inverse, LU, Eigen, Diagonalization (Lec 11–13)

**Inverse.** Exists $\iff\det A\neq0$. $\left(\begin{smallmatrix}a&b\\c&d\end{smallmatrix}\right)^{-1}=\frac{1}{ad-bc}\left(\begin{smallmatrix}d&-b\\-c&a\end{smallmatrix}\right)$.
- **Gauss–Jordan:** $(A|I)\to(I|A^{-1})$. Clear columns top to bottom, then bottom to top. Swaps are OK.
- **Adjugate:** $A^{-1}=\frac{1}{\det A}\text{adj}A$, where adj is the **transpose** of the cofactor matrix (cofactor $A_{ij}$ goes to $(j,i)$).
- $(AB)^{-1}=B^{-1}A^{-1}$, $(A^T)^{-1}=(A^{-1})^T$. **Check** one row of $AA^{-1}$, or use the calculator's matrix mode.
- **Cramer:** $x_i=\det A^{(i)}/\det A$, where $A^{(i)}$ is column $i$ replaced by $\mathbf c$.

**LU** ($l_{ii}=1$; $L$ lower, $U$ upper):
1. Eliminate **without swaps**. $l_{ij}$ = (entry being eliminated) ÷ (current pivot). Do $R_i-l_{ij}R_j$.
2. Put $l_{ij}$ into $L$ at $(i,j)$ and **keep its sign** ($6\div(-3)=-2$). $U$ is the final echelon matrix.
3. Solve $L\mathbf y=\mathbf c$ (forward), then $U\mathbf x=\mathbf y$ (back).
- **Check:** row 3 of $L$ times $U$ = row 3 of $A$.

**Eigenvalues.** $A\mathbf x=\lambda\mathbf x$, $\mathbf x\neq\mathbf 0$. Solve $\det(\lambda I-A)=0$. The eigenvectors are the null space of $A-\lambda I$, and any non-zero multiple also works.
- $2\times2$: $\lambda^2-(\text{tr}A)\lambda+\det A$
- $3\times3$: $\lambda^3-(\text{tr}A)\lambda^2+(M_{11}+M_{22}+M_{33})\lambda-\det A$, where the $M_{ii}$ are the diagonal $2\times2$ minors. Example (practice Q6): $10$, $7+7+7$, $0$ gives $\lambda(\lambda-3)(\lambda-7)$.
- To factor, try integer roots that divide the constant term, then use synthetic division.
- **Check** $\sum\lambda=\text{tr}A$ and $\prod\lambda=\det A$. $\lambda=0\iff A$ is singular. Triangular: $\lambda$ = the diagonal.
- **Cross-product trick** (3×3, simple $\lambda$): the eigenvector is (row $i$) × (row $j$) of $A-\lambda I$, for any two non-parallel rows. Then check $A\mathbf v=\lambda\mathbf v$.

**Symmetric $A$.** The $\lambda$ are real. A $k$-fold $\lambda$ has $k$ independent eigenvectors. Eigenvectors for **different** $\lambda$ are orthogonal, and together they form an orthogonal basis.
- A repeated $\lambda$ is **not** automatically orthogonal: run Gram–Schmidt inside its eigenspace. Example for the plane $x_1+x_2+x_3=0$: $(-1,1,0)$ and $(-1,0,1)$ become $(-1,1,0)$ and $(-1,-1,2)$.

**Diagonalization.** $Q^{-1}AQ=D\iff n$ LI eigenvectors. $Q=(\mathbf e_1|\cdots|\mathbf e_n)$ and $D=\text{diag}(\lambda_i)$ **in the same order**.
- It always works for $n$ distinct $\lambda$ or symmetric $A$. It fails if a repeated $\lambda$ has too few eigenvectors, e.g. $\left(\begin{smallmatrix}2&1\\0&2\end{smallmatrix}\right)$.
- **"$Q^TAQ=D$" means NORMALIZE the columns.** Then $Q^{-1}=Q^T$, $A=QDQ^T$, $A^k=QD^kQ^T$.
- Write out the full $Q$ **and** $D$. **Check** that the columns are unit length and pairwise orthogonal.

**Quadratic forms.** $f=\mathbf x^TA\mathbf x$ with $A$ symmetric. The off-diagonal entry is **half** the cross-term coefficient:
$$ax_1^2+bx_2^2+cx_3^2+2dx_1x_2+2ex_1x_3+2fx_2x_3\ \longleftrightarrow\ A=\begin{pmatrix}a&d&e\\d&b&f\\e&f&c\end{pmatrix}$$
- With $\tilde{\mathbf x}=Q^T\mathbf x$: $f=\sum\lambda_i\tilde x_i^2$.
- All $\lambda>0$: positive definite. All $\lambda\ge0$ with some $\lambda=0$: positive semi-definite. Mixed signs: indefinite.

**Unit-vector values:**

| $\tfrac{1}{\sqrt2}$ | $\tfrac{1}{\sqrt3}$ | $\tfrac{1}{\sqrt5}$ | $\tfrac{1}{\sqrt6}$ | $\tfrac{2}{\sqrt6}$ | $\tfrac{1}{\sqrt{14}}$ | $\tfrac{1}{\sqrt{42}}$ |
|---|---|---|---|---|---|---|
| 0.7071 | 0.5774 | 0.4472 | 0.4082 | 0.8165 | 0.2673 | 0.1543 |

**Strategy.** Read all six and rank them (2 min). Allow about 17 minutes each. If you're stuck for 5 minutes, write the setup and method for partial credit, then move on. Use leftover time on a 5th problem, since only the best 4 count.
