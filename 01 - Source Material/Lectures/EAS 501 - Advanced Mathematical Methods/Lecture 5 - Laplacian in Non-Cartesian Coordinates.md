2026-09-21 09:47

Course: #eas501 

## Big Ideas

*quick summary of ideas - 3-5 bullet points max*

## Key Concepts

*place links to full notes here*

## Notes

### Summary
- **Coordinate systems**
	- Polar: $x = r\cos\theta,\ y = r\sin\theta$
	- Cylindrical: polar plus $z = z$
	- Spherical: $x = \rho\sin\phi\cos\theta,\ y = \rho\sin\phi\sin\theta,\ z = \rho\cos\phi$
	- $\phi$ is measured down from the $+z$ axis.
- **Goal:** rewrite the Laplacian $\Delta u = u_{xx} + u_{yy}$ in terms of $r, \theta$. $\Delta$ is the Laplacian, *not* "change in $u$."
- **Step 1, inverse partials:** from $r = \sqrt{x^2+y^2}$ and $\theta = \tan^{-1}(y/x)$:
$$r_x = \cos\theta,\quad r_y = \sin\theta,\quad \theta_x = -\frac{\sin\theta}{r},\quad \theta_y = \frac{\cos\theta}{r}$$
- **Step 2, chain rule once:**
$$u_x = \cos\theta\, u_r - \frac{\sin\theta}{r}\, u_\theta, \qquad u_y = \sin\theta\, u_r + \frac{\cos\theta}{r}\, u_\theta$$
- **Step 3, chain rule twice:** differentiate $u_x$ with respect to $x$ again. You need the product rule because the coefficients $\cos\theta$ and $-\sin\theta/r$ also depend on $x$.
- **Step 4, add $u_{xx} + u_{yy}$:** the mixed $u_{r\theta}$ terms and the $u_\theta$ terms cancel, and $\sin^2 + \cos^2 = 1$ cleans up the rest:
$$\boxed{\Delta u = u_{rr} + \frac{1}{r}u_r + \frac{1}{r^2}u_{\theta\theta} = \frac{1}{r}\frac{\partial}{\partial r}\!\left(r\,\frac{\partial u}{\partial r}\right) + \frac{1}{r^2}\frac{\partial^2 u}{\partial\theta^2}}$$
- **3-D versions:**
	- Cylindrical: add $u_{zz}$ to the polar formula.
	- Spherical:
$$\Delta u = \frac{1}{\rho^2}\left[\frac{\partial}{\partial\rho}\!\left(\rho^2 \frac{\partial u}{\partial\rho}\right) + \frac{1}{\sin\phi}\frac{\partial}{\partial\phi}\!\left(\sin\phi\,\frac{\partial u}{\partial\phi}\right) + \frac{1}{\sin^2\phi}\frac{\partial^2 u}{\partial\theta^2}\right]$$

> [!tip] Intuition
> $\Delta u$ measures how $u$ at a point compares to the average of its neighbors. $\Delta u = 0$ (harmonic) means there is no local bump or dip. The extra $\tfrac1r u_r$ term appears because polar grid lines spread apart as $r$ grows. It comes from differentiating the *coefficients* $\cos\theta$ and $-\sin\theta/r$ in Step 3, not from $u$ itself.

> [!warning] Slide typos / notation
> - Eqs. (10) and (11) write $\frac{\partial^2 u}{\partial y^2} + \frac{\partial^2 u}{\partial y^2}$. The first term should be $\frac{\partial^2 u}{\partial x^2}$.
> - The slides write $\frac{\partial^2 u}{\partial^2 r}$. Standard notation is $\frac{\partial^2 u}{\partial r^2}$.
> - Some textbooks swap the roles of $\phi$ and $\theta$ in spherical coordinates (physics vs. math convention). Check which one a source uses.

---
### Worked Examples

Ex 1: Sanity check, $u = x^2 + y^2 = r^2$
- Cartesian: $\Delta u = 2 + 2 = 4$
- Polar: $u_r = 2r$, $u_{rr} = 2$, $u_{\theta\theta} = 0$
$$\Delta u = 2 + \tfrac{1}{r}(2r) + 0 = 4 \checkmark$$

Ex 2: Angular dependence, $u = r^2\cos 2\theta$ (which equals $x^2 - y^2$)
- $u_{rr} = 2\cos2\theta$
- $\tfrac1r u_r = 2\cos 2\theta$
- $\tfrac{1}{r^2}u_{\theta\theta} = \tfrac{1}{r^2}(-4r^2\cos2\theta) = -4\cos2\theta$
- Sum: $\Delta u = 0$, so $u$ is harmonic. Cartesian check: $2 - 2 = 0$ ✓

Ex 3: Why polar pays off, $u = \ln r = \tfrac12\ln(x^2+y^2)$
- Polar: $u_r = \tfrac1r$, $u_{rr} = -\tfrac{1}{r^2}$
$$\Delta u = -\tfrac{1}{r^2} + \tfrac{1}{r^2} = 0 \quad (r \neq 0)$$
- In Cartesian this takes a page of quotient rules. In polar it takes two lines.

Ex 4: Likely test style — find all radial harmonic functions in 2-D
- Assume $u = u(r)$ only, so $u_{\theta\theta} = 0$:
$$\frac{1}{r}\big(r\,u'\big)' = 0 \;\Rightarrow\; r\,u' = C_1 \;\Rightarrow\; u = C_1\ln r + C_2$$

Ex 5: Spherical
- $u = \rho^2$:
$$\Delta u = \frac{1}{\rho^2}\big(\rho^2\cdot 2\rho\big)' = \frac{6\rho^2}{\rho^2} = 6$$
  This matches Cartesian $2+2+2$ ✓
- $u = \frac{1}{\rho}$:
$$\big(\rho^2\cdot(-\rho^{-2})\big)' = (-1)' = 0 \;\Rightarrow\; \Delta u = 0$$
  This is the gravitational/Coulomb potential, which is harmonic away from the origin.

Test Strategy
- For a function of $r$ (or $\rho$) only, drop the angular terms and use the compact form $\tfrac{1}{r}(r u_r)_r$ or $\tfrac{1}{\rho^2}(\rho^2 u_\rho)_\rho$.
- If $u$ is easy to write in $x, y$, check your answer in Cartesian.
- Know Steps 1–2 cold. A likely short question is "derive $u_x$ in polar."

## Questions/Gaps/Concerns



## Follow-up 

*actions items to follow-up on (e.g., watch video, re-read notes, hw)*



## References

*link to other notes, attachments, or actual lecture slides*
- [[Lec0921_2026.pdf]]