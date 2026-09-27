2026-09-14 18:20

Course:

## Big Ideas

*quick summary of ideas - 3-5 bullet points max*

## Key Concepts

*place links to full notes here*

## Notes

#### Lecture Summary: Ch. 14, Vectors in Three Dimensions (09/14)

- Dot product (14.2–14.3): For $\mathbf{u} = (x_1, y_1, z_1)^T$ and $\mathbf{v} = (x_2, y_2, z_2)^T$, the geometric and analytic definitions agree:

	- $$\mathbf{u}\cdot\mathbf{v} = |\mathbf{u}||\mathbf{v}|\cos\theta = x_1x_2 + y_1y_2 + z_1z_2.$$
	- The result is a scalar that measures how aligned the two vectors are.
- Cross product: Geometrically, $\mathbf{u}\times\mathbf{v} = \big(|\mathbf{u}||\mathbf{v}|\sin\theta\big)\,\mathbf{n}$, where $\mathbf{n}$ is the unit normal given by the right-hand rule. Analytically, you compute it by cofactor expansion of a determinant:

	- $$\mathbf{u}\times\mathbf{v} = \begin{vmatrix} \mathbf{i} & \mathbf{j} & \mathbf{k} \\ x_1 & y_1 & z_1 \\ x_2 & y_2 & z_2 \end{vmatrix} = \begin{pmatrix} y_1z_2 - y_2z_1 \\ x_2z_1 - x_1z_2 \\ x_1y_2 - x_2y_1 \end{pmatrix}.$$
	- Remember the minus sign on the $\mathbf{j}$ term.
- Cross product as area: $|\mathbf{u}\times\mathbf{v}| = |\mathbf{u}||\mathbf{v}|\sin\theta$ is the area of the parallelogram spanned by $\mathbf{u}$ and $\mathbf{v}$. A triangle is half of that parallelogram, so

	- $$S_{\triangle ABC} = \tfrac{1}{2}\big|\overrightarrow{AB}\times\overrightarrow{AC}\big|.$$
- Multiple products (14.4): The scalar triple product $\mathbf{u}\cdot(\mathbf{v}\times\mathbf{w})$ gives the signed volume of a parallelepiped. The vector triple product is not associative, $(\mathbf{u}\times\mathbf{v})\times\mathbf{w} \neq \mathbf{u}\times(\mathbf{v}\times\mathbf{w})$, and it satisfies the "BAC–CAB" identity:

	- $$\mathbf{u}\times(\mathbf{v}\times\mathbf{w}) = (\mathbf{u}\cdot\mathbf{w})\,\mathbf{v} - (\mathbf{u}\cdot\mathbf{v})\,\mathbf{w}.$$
- Example 14.4 #1(b): With $\mathbf{u} = (1,-1,0)^T$, $\mathbf{v} = (2,1,3)^T$, $\mathbf{w} = (0,1,-1)^T$, you get $\mathbf{u}\times(\mathbf{v}\times\mathbf{w}) = (-2,-2,-2)^T$ but $(\mathbf{u}\times\mathbf{v})\times\mathbf{w} = (0,-3,-3)^T$, a concrete case of non-associativity. BAC–CAB checks the first result: $(-1)(2,1,3)^T - (1)(0,1,-1)^T = (-2,-2,-2)^T$.
- Differentiating vector functions (14.5): For $\mathbf{r}(t) = (x(t), y(t), z(t))^T$, you differentiate componentwise, $\mathbf{r}'(t) = (x', y', z')^T$, and the unit tangent is $\mathbf{T}(t) = \mathbf{r}'(t)/|\mathbf{r}'(t)|$. If $\mathbf{r}$ is position, then $\mathbf{v} = \mathbf{r}'$ is velocity and $\mathbf{a} = \mathbf{r}''$ is acceleration.
- Example 14.5 #1(e): For $\mathbf{u}(\tau) = \big(e^{-\tau}\cos 2\tau,\ e^{-\tau}\sin 2\tau\big)^T$ (a decaying spiral), the product rule gives $\mathbf{u}''$, and the cross terms cancel when you square and add:
	- The product rule is given by: f'(x)g(x) + f(x)g'(x)
	- The inner terms simplify to $\sin^2(2\tau)+\cos^2(2\tau)$, which is 1
	- $$|\mathbf{u}''(\tau)| = \sqrt{25e^{-2\tau}} = 5e^{-\tau}. $$
---
#### Example 1: 14.3 #4 (b)

- Find the area of triangle $\triangle ABC$ with vertices: A(2, -2, 1), B(4, 0, 3), C(2, 3, 5)
- Step 1: Build edge vectors from a common vertex. The vectors must share a starting point, here $A$. Subtract the start from the end:
	- $$
\vec{AB} = B-A=(4-2), (0-(-2)), (3-1), \vec{AB} = (2,2,2)^T, \vec{AC} = C-A=(0,5,4)^T
$$
- Step 2: Cross product:
	- $$
\begin{gather}
\vec{n} = \overrightarrow{AB} \times\overrightarrow{AC} \\
\mathbf{n} = \begin{vmatrix} \mathbf{i} & \mathbf{j} & \mathbf{k} \\ 2 & 2 & 2 \\ 0 & 5 & 4 \end{vmatrix} = \mathbf{i}(8-10) - \mathbf{j}(8-0) + \mathbf{k}(10-0) = (-2,-8,10)^T.
\end{gather}
$$
- Step 3: magnitude and half (basic triangle equations)
	- $$S_{\triangle ABC} = \tfrac{1}{2}\sqrt{4 + 64 + 100} = \tfrac{1}{2}\sqrt{168} = \tfrac{1}{2}\sqrt{4\cdot 42} = \sqrt{42}.$$
	- Equation provided in slides as:
	- $$
\frac{1}{2}|\overrightarrow{AB}| *|\overrightarrow{AC}| *\sin A=\frac{1}{2}|n|
$$
	- There is a way to prove the above statement using dot product
	- Ignore the 1/2 since both sides have that
	- Basically just solve for cos from the dot product and then perform substitutions

---
#### Example 2: Volume of a Parallelpiped

The drawing is a bit cramped, so here's how to read it. All three vectors start at the bottom-left corner.

- $\mathbf{v}$ runs along the bottom edge, to the right.
- $\mathbf{w}$ runs into the page, at angle $\varphi$ from $\mathbf{v}$. Together $\mathbf{v}$ and $\mathbf{w}$ span the **base** parallelogram, labeled $A$.
- $\mathbf{u}$ is the slanted edge going up. The "$u/\vec w$" labeling on the slide is just the two arrows drawn close together.
- $\mathbf{n} = \mathbf{v}\times\mathbf{w}$ points straight up, perpendicular to the base. $\theta$ is the angle between $\mathbf{u}$ and $\mathbf{n}$, **not** between $\mathbf{u}$ and the base.

**Step 1: Base area.** This is the same fact as in Clarification 1:  

$$A = |\mathbf{v}||\mathbf{w}|\sin\varphi = |\mathbf{v}\times\mathbf{w}|.$$

**Step 2: Height.** Because $\mathbf{u}$ is slanted, the height is not $|\mathbf{u}|$. It's the component of $\mathbf{u}$ along the vertical direction $\mathbf{n}$. Since $\theta$ is measured from the vertical:  

$$h = |\mathbf{u}|\cos\theta.$$

**Step 3: Volume = base × height.** The key move is recognizing a dot product:  

$$V = A\cdot h = |\mathbf{v}\times\mathbf{w}|\,|\mathbf{u}|\cos\theta = \mathbf{u}\cdot(\mathbf{v}\times\mathbf{w}),$$

because $|\mathbf{u}||\mathbf{n}|\cos\theta$ is exactly the geometric definition of $\mathbf{u}\cdot\mathbf{n}$. The cross product supplies the base area and the direction perpendicular to the base; the dot product then projects $\mathbf{u}$ onto that direction to get the height.

**About the absolute value.** The slide writes $|\mathbf{u}\cdot(\mathbf{v}\times\mathbf{w})|$. If $\mathbf{u}$ points to the opposite side of the base from $\mathbf{n}$, then $\cos\theta < 0$ and the triple product comes out negative. So the triple product is a _signed_ volume, where the sign encodes orientation (right- vs. left-handed ordering), and physical volume takes the absolute value.

**Useful consequences for your notes:**

- The triple product equals a determinant:  
    $$\mathbf{u}\cdot(\mathbf{v}\times\mathbf{w}) = \begin{vmatrix} u_1 & u_2 & u_3 \\ v_1 & v_2 & v_3 \\ w_1 & w_2 & w_3 \end{vmatrix}.$$
- **Cyclic symmetry:** $\mathbf{u}\cdot(\mathbf{v}\times\mathbf{w}) = \mathbf{v}\cdot(\mathbf{w}\times\mathbf{u}) = \mathbf{w}\cdot(\mathbf{u}\times\mathbf{v})$. It's the same box whichever face you call the base.
- **Coplanarity test:** $\mathbf{u}\cdot(\mathbf{v}\times\mathbf{w}) = 0$ exactly when the three vectors lie in one plane, because the box has been flattened to zero volume.

For the lecture's own vectors, $\mathbf{u}\cdot(\mathbf{v}\times\mathbf{w}) = (1,-1,0)\cdot(-4,2,2) = -6$. So those three vectors span a box of volume $6$, and the negative sign means they're in left-handed order.

---



## Questions/Gaps/Concerns



## Follow-up 

*actions items to follow-up on (e.g., watch video, re-read notes, hw)*



## References

*link to other notes, attachments, or actual lecture slides*
- [[Lec0914_2026.pdf]]