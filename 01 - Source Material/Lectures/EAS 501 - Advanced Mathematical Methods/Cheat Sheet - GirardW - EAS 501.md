### Leibniz Rule (13.8)

$$\frac{d}{dt}\int_{a(t)}^{b(t)} f(x,t)\,dx = \int_{a(t)}^{b(t)} f_t(x,t)\,dx \;+\; b'(t)\,f(b(t),t) \;-\; a'(t)\,f(a(t),t)$$

- There are three pieces: the interior term, the upper-limit gain, and the lower-limit loss. A constant limit contributes $0$.
- The slide example $\frac{d^2}{dx^2}\int_x^{2x}\ln(u^2+x^2)\,du = \frac{2}{x}$ uses two passes. Apply Leibniz once, evaluate the boundary terms, then differentiate again.
- To check your answer, use the substitution $u = xs$ (limits become constants), or integrate first if the integral is doable.
- **Pitfall:** if you substitute inside the integral, **change the limits**.

### Taylor with Lagrange Remainder (13.5)

$$f(x) = \sum_{k=0}^{n-1}\frac{f^{(k)}(a)}{k!}(x-a)^k + \frac{f^{(n)}(\xi)}{(n)!}(x-a)^{n},\quad \xi \text{ between } a, x$$

- Error bound: $|R| \le \dfrac{\max|f^{(n+1)}|}{(n+1)!}\max|x-a|^{n+1}$.
- **Skip trick:** for sin and cos centered at 0, alternate coefficients are zero, so $P_3 = P_4$ for $\sin$ and $P_2 = P_3$ for $\cos$. Use the next remainder for a tighter bound (slide: $\sin x$ on $[0,0.5]$ gives $|R| \le 0.5^5/5!$).
- **Rounding rule:** round error bounds **up**, round a maximum $h$ **down**, and round a minimum $n$ **up**.
- 2D version:  
    $$f(x,y) \approx f + f_x\,\Delta x + f_y\,\Delta y + \tfrac{1}{2}\left[f_{xx}\Delta x^2 + 2f_{xy}\Delta x\Delta y + f_{yy}\Delta y^2\right]$$

### Implicit Function Theorem (13.6)

- **One equation:** if $F(x_0,y_0)=0$ and $F_y(x_0,y_0)\neq 0$, then $y(x)$ exists locally and $\dfrac{dy}{dx} = -\dfrac{F_x}{F_y}$.
- **System:** for $x = x(u,v)$, $y = y(u,v)$, you can solve locally for $u(x,y), v(x,y)$ if  
    $$\det J = \det\begin{pmatrix} x_u & x_v \\ y_u & y_v\end{pmatrix} \neq 0.$$
- Then $\begin{pmatrix} u_x & u_y \\ v_x & v_y\end{pmatrix} = J^{-1}$, where $\begin{pmatrix} a & b \\ c & d\end{pmatrix}^{-1} = \dfrac{1}{ad-bc}\begin{pmatrix} d & -b \\ -c & a\end{pmatrix}$.
- Slide example: $x = u\cos v$, $y = u\sin v$ at $(x,y,u,v)=(0,2,2,\pi/2)$ gives $\det J = u = 2 \neq 0$.

### Lagrange Multipliers: Closest Point (13.7)

- Minimize the **squared** distance $f = (x-x_0)^2 + (y-y_0)^2+(z-z_{0})^2$ subject to $g = 0$.
- Solve $\nabla f = \lambda\nabla g$ together with $g = 0$. Write each coordinate in terms of $\lambda$, substitute into the constraint, and solve for $\lambda$.
- Slide example: $(1,-2)$ to the line $x+y=-5$ gives $\lambda=-4$ and closest point $(-1,-4)$.
- Check with the distance formula: $d = \dfrac{|ax_0+by_0+cz_0 - d|}{\sqrt{a^2+b^2+c^2}}$. The answer is the foot of the perpendicular.

### Unconstrained Extrema (13.7)

- Set $\nabla f = \mathbf{0}$ to find critical points, then examine the Hessian $H = \begin{pmatrix} f_{xx} & f_{xy} \\ f_{xy} & f_{yy}\end{pmatrix}$.
- Positive definite (all eigenvalues $>0$) means a **min**. Negative definite means a **max**. Mixed signs mean a **saddle**. If $\det H = 0$, the test is inconclusive.
- 2×2 shortcut: $\det H>0$ with $f_{xx}>0$ is a min, and $\det H>0$ with $f_{xx}<0$ is a max. $\det H<0$ is a saddle.

## Cheat Sheet (Back): Everything Else

### Partials, Clairaut, Chain Rule (13.3–13.4)

- **Clairaut:** if $f_x, f_y, f_{xy}, f_{yx}$ are continuous on an open set around the point, then $f_{xy}=f_{yx}$.
- Justification sentence: "polynomials, exp, sin, and cos are continuous everywhere, and rational functions are continuous where the denominator is nonzero."
- Counterexample: $f = \dfrac{xy(x^2-y^2)}{x^2+y^2}$ with $f(0,0)=0$ has $f_{xy}(0,0) = -1 \neq 1 = f_{yx}(0,0)$. Near the origin, use the limit definition directly.
- **Chain rule:** $\dfrac{dF}{dt} = \sum_i \dfrac{\partial f}{\partial x_i}\dfrac{dx_i}{dt}$. Plug in the point first, then evaluate.

### Vectors (Ch. 14)

- $\mathbf{a}\cdot\mathbf{b} = |\mathbf{a}||\mathbf{b}|\cos\theta$ and $|\mathbf{a}\times\mathbf{b}| = |\mathbf{a}||\mathbf{b}|\sin\theta$.
- Triangle area $= \tfrac12|\vec{AB}\times\vec{AC}|$.
- Parallelepiped volume $= |\mathbf{a}\cdot(\mathbf{b}\times\mathbf{c})| = |\det[\mathbf{a};\mathbf{b};\mathbf{c}]|$. A triple product of $0$ means the vectors are coplanar.
- BAC–CAB: $\mathbf{a}\times(\mathbf{b}\times\mathbf{c}) = \mathbf{b}(\mathbf{a}\cdot\mathbf{c}) - \mathbf{c}(\mathbf{a}\cdot\mathbf{b})$.

### Fields (16.2–16.6)

- $\nabla f = (f_x,f_y,f_z)$ points in the direction of steepest ascent, and the max rate is $|\nabla f|$.
- $D_{\mathbf{a}}f = \nabla f\cdot\dfrac{\mathbf{v}}{|\mathbf{v}|}$. **Normalize first.**
- $\nabla\cdot\mathbf{F} = P_x+Q_y+R_z$. A value of $0$ means incompressible.
- $\nabla\times\mathbf{F} = (R_y-Q_z,\;P_z-R_x,\;Q_x-P_y)$.
- Two identities are always zero: $\nabla\times\nabla f = \mathbf{0}$ and $\nabla\cdot(\nabla\times\mathbf{F}) = 0$.
- Laplacian: $\Delta f = f_{xx}+f_{yy}+f_{zz}$.

### Laplacian in Other Coordinates (16.7)

- Inverse partials: $r_x=\cos\theta$, $r_y = \sin\theta$, $\theta_x = -\sin\theta/r$, $\theta_y = \cos\theta/r$.
- Polar:  
    $$\Delta u = u_{rr} + \tfrac1r u_r + \tfrac{1}{r^2}u_{\theta\theta} = \tfrac1r(r u_r)_r + \tfrac{1}{r^2}u_{\theta\theta}$$
- For cylindrical coordinates, add $u_{zz}$.
- Spherical, radial part only: $\tfrac{1}{\rho^2}(\rho^2 u_\rho)_\rho$.
- Radial harmonic functions: $u = C_1\ln r + C_2$ in 2D and $u = C_1/\rho + C_2$ in 3D.