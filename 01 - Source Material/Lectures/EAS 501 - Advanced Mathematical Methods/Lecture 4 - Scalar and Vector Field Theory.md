2026-09-16 07:49

Course: #eas501

## Big Ideas

*quick summary of ideas - 3-5 bullet points max*

## Key Concepts

*place links to full notes here*

## Notes

### Slide Summary:

#### 16.2 Preliminaries
- A **scalar field** assigns a number to each point: $f(x,y)$ or $f(x,y,z)$.
- A **vector field** assigns a vector to each point: $\mathbf{F}(x,y,z) = (f_1, f_2, f_3)^T$, often written $(P, Q, R)^T$.

#### 16.3 Divergence
- For $\mathbf{F} = (P,Q,R)^T$: $\;\nabla \cdot \mathbf{F} = P_x + Q_y + R_z$ (a scalar).
- Measures net "outflow" at a point; $\nabla \cdot \mathbf{F} = 0$ means the field is **incompressible** (no sources or sinks).
- **Ex. 16.3 #2:** flow past a cylinder of radius $a$ with far-field speed $U$:
$$\mathbf{v} = U\mathbf{i} + \frac{Ua^2}{(x^2+y^2)^2}\big((y^2-x^2)\mathbf{i} - 2xy\,\mathbf{j}\big)$$
  Using the quotient rule on $P$ and $Q$, the terms cancel and $\nabla \cdot \mathbf{v} = 0$.

#### 16.4 Gradient and Directional Derivative
- $\nabla f = (f_x, f_y, f_z)^T$ (a vector); it points in the direction of steepest increase.
- May also be written as: $\nabla = \frac{\partial}{\partial x}\vec{i}+\frac{\partial}{\partial y}\vec{j}+\frac{\partial}{\partial z}\vec{k}$
- Directional derivative along a **unit** vector $\mathbf{a}$: $\;D_{\mathbf{a}} f = \nabla f \cdot \mathbf{a}$.
- If the given direction $\mathbf{v}$ isn't unit length, normalize first: $\mathbf{a} = \mathbf{v}/|\mathbf{v}|$.
- Partial derivatives computed easily: $f_{x} = (xyz)'=yz$
- **Ex. 16.4 #2(c):** $f = xyz$, $P = (1,-1,2)$, $\mathbf{v} = (3,0,-1)^T$
  - $\nabla f = (yz, xz, xy)^T \Rightarrow \nabla f(P) = (-2, 2, -1)^T$
  - $\mathbf{a} = \tfrac{1}{\sqrt{10}}(3, 0, -1)^T$
  - $D_{\mathbf{a}} f = \tfrac{-6 + 0 + 1}{\sqrt{10}} = -\tfrac{5}{\sqrt{10}}$

#### 16.5 Curl
- $\nabla \times \mathbf{F} = (R_y - Q_z,\; P_z - R_x,\; Q_x - P_y)^T$ (a vector); measures local rotation.
	- The above definition defines the cross-product between $\nabla$ and $\mathbf{F}$
	- The $R_{y}$ means take the derivative of R w.r.t. y
- The curl of a gradient is always zero: $\nabla \times (\nabla f) \equiv \mathbf{0}$.
- **Ex. 16.5 #1(e):** $\mathbf{v} = (xy,\, 0,\, -2(x^2+z^2))^T \Rightarrow \nabla \times \mathbf{v} = (0,\, 4x,\, -x)^T$

#### 16.6 Identities and the Laplacian
- Product rules:
  - $\nabla \cdot (f\mathbf{v}) = \nabla f \cdot \mathbf{v} + f(\nabla \cdot \mathbf{v})$
  - $\nabla \times (f\mathbf{v}) = \nabla f \times \mathbf{v} + f(\nabla \times \mathbf{v})$
  - $\nabla \cdot (\mathbf{u} \times \mathbf{v}) = \mathbf{v} \cdot (\nabla \times \mathbf{u}) - \mathbf{u} \cdot (\nabla \times \mathbf{v})$
  - $\nabla \times (\mathbf{u} \times \mathbf{v}) = \mathbf{u}(\nabla \cdot \mathbf{v}) - \mathbf{v}(\nabla \cdot \mathbf{u}) + (\mathbf{v} \cdot \nabla)\mathbf{u} - (\mathbf{u} \cdot \nabla)\mathbf{v}$
  - $\nabla(\mathbf{u} \cdot \mathbf{v}) = (\mathbf{u} \cdot \nabla)\mathbf{v} + (\mathbf{v} \cdot \nabla)\mathbf{u} + \mathbf{u} \times (\nabla \times \mathbf{v}) + \mathbf{v} \times (\nabla \times \mathbf{u})$
- Laplacian: $\Delta f = \nabla \cdot (\nabla f) = f_{xx} + f_{yy} + f_{zz}$
- Always zero: $\nabla \cdot (\nabla \times \mathbf{v}) = 0$ and $\nabla \times (\nabla f) = \mathbf{0}$
- Curl of curl: $\nabla \times (\nabla \times \mathbf{v}) = \nabla(\nabla \cdot \mathbf{v}) - \Delta \mathbf{v}$
- **Ex. 16.6 #1(e):** $u = xe^y \Rightarrow \Delta u = 0 + xe^y = xe^y$; and $\nabla u = (e^y, xe^y)^T$, so $\nabla \times \nabla u = \mathbf{0}$ (as the identity says).

> [!note] Notation
> The slides write $\mathbf{v} \cdot \nabla \mathbf{u}$. This means $(\mathbf{v} \cdot \nabla)\mathbf{u}$: apply the operator $v_1\partial_x + v_2\partial_y + v_3\partial_z$ to each component of $\mathbf{u}$. $\Delta \mathbf{v}$ means taking the Laplacian of each component.

---
### Example Problems

#### Problem 1 (similar to Example 16.3 #2)

Compute $\nabla \cdot \mathbf{v}$ for

$$\mathbf{v}(x,y) = U\mathbf{i} + \frac{k}{x^2+y^2}\big(x,\mathbf{i} + y,\mathbf{j}\big)$$

where $U$ and $k$ are constants.

**Physical meaning:** This is uniform flow at speed $U$ plus a **source** at the origin that pushes fluid outward in all directions, with strength set by $k$. As in the slide example, $U$ and $k$ are parameters, not variables.

1) Identify $P$ and $Q$

	- Collect the $\mathbf{i}$ and $\mathbf{j}$ parts:
		- P --> i, Q --> j, R --> k
	- $$P = U + \frac{kx}{x^2+y^2}, \qquad Q = \frac{ky}{x^2+y^2}$$
	- The divergence in 2-D is $\nabla \cdot \mathbf{v} = P_x + Q_y$.
		- 3-D is $\nabla * \mathbf{F} = P_{x}+Q_{y}+R_{z}$

2) Step 2: Compute $P_x$

	- The $U$ term is a constant, so its derivative is $0$. The $\mathbf{i}$ term in the slide example worked the same way.
	- For the fraction, use the quotient rule, $\left(\frac{f}{g}\right)' = \frac{f'g - fg'}{g^2}$, with $f = kx$ and $g = x^2+y^2$. Treat $y$ as a constant:
		- $f_x = k$
		- $g_x = 2x$
		- $$P_x = 0 + \frac{k(x^2+y^2) - kx(2x)}{(x^2+y^2)^2}$$
	- Simplify the numerator:
		- $$k(x^2+y^2) - 2kx^2 = k(y^2 - x^2)$$
	- So
		- $$P_x = \frac{k(y^2-x^2)}{(x^2+y^2)^2}$$
3) Compute $Q_y$

	- Use the same quotient rule with $f = ky$ and $g = x^2+y^2$. This time treat $x$ as a constant:
		- $f_y = k$
		- $g_y = 2y$
		- $$Q_y = \frac{k(x^2+y^2) - ky(2y)}{(x^2+y^2)^2} = \frac{k(x^2-y^2)}{(x^2+y^2)^2}$$

4) Add them

	- $$\nabla \cdot \mathbf{v} = \frac{k(y^2-x^2)}{(x^2+y^2)^2} + \frac{k(x^2-y^2)}{(x^2+y^2)^2} = \frac{k\big[(y^2-x^2)+(x^2-y^2)\big]}{(x^2+y^2)^2} = 0$$
- Result:
$$\nabla \cdot \mathbf{v} = 0 \quad \text{for } (x,y) \neq (0,0)$$

The flow is incompressible everywhere except the origin. The field isn't defined at the origin, and that's where the source is creating fluid.

## Questions/Gaps/Concerns



## Follow-up 

*actions items to follow-up on (e.g., watch video, re-read notes, hw)*



## References

*link to other notes, attachments, or actual lecture slides*
- [[Lec0916_2026.pdf]]