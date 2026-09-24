2026-09-09 13:47

Course: #eas501

## Big Ideas

*quick summary of ideas - 3-5 bullet points max*

## Key Concepts

*place links to full notes here*

## Notes

### 13.7 Maximum and Minimum Values

- **Single-variable case:** if $f(x)$ has a local extreme at $x_0$ and is differentiable there, then $f'(x_0) = 0$ — the usual first-order condition.
- **Higher-order test:** if the first $n-1$ derivatives vanish at $x_0$ but $f^{(n)}(x_0) \neq 0$, then for even $n$: negative $f^{(n)}(x_0)$ gives a local max, positive gives a local min. For odd $n$, $x_0$ is a horizontal inflection point instead.
- **Multivariable case:** at a local extreme of $f(x_1,\dots,x_n)$, all first partials vanish simultaneously: $f_{x_1} = f_{x_2} = \cdots = f_{x_n} = 0$.
- **Second-order test (Hessian):** build the Hessian matrix $A$ of second partials at the critical point. If $\det A \neq 0$: $A$ positive definite $\Rightarrow$ local min, $A$ negative definite $\Rightarrow$ local max, and mixed-sign eigenvalues $\Rightarrow$ saddle point.
- This is the direct multivariable analogue of the single-variable second-derivative test — eigenvalue sign replaces the sign of $f''$.

### Constrained Extrema & Lagrange Multipliers

- **Setup:** optimize $f(x_1,\dots,x_n)$ subject to $g(x_1,\dots,x_n) = 0$, equivalent to unconstrained optimization of $f^* := f - \lambda g$.
- **Lagrange conditions:** solve the system $\nabla f - \lambda \nabla g = 0$ together with $g = 0$.
- **Worked example (13.7 #16b):** minimize distance from $(1,-2)$ to the line $x+y=-5$, i.e. minimize $f(x,y) = (x-1)^2 + (y+2)^2$ subject to $g(x,y) = x+y+5=0$.
- Setting up $\nabla f = \lambda \nabla g$ gives $x = 1+\tfrac{\lambda}{2}$ and $y = -2+\tfrac{\lambda}{2}$; substituting into the constraint solves $\lambda = -4$.
- **Result:** the closest point is $(-1,-4)$ — a clean geometric check is that this is just the foot of the perpendicular from $(1,-2)$ to the line.

### 13.8 Leibniz Rule — the trickier part

- The general **Leibniz rule** handles differentiating an integral whose *integrand and both limits* all depend on the variable you're differentiating with respect to:

$$\frac{d}{dt}\int_{a(t)}^{b(t)} f(x,t)\,dx = \int_{a(t)}^{b(t)} f_t(x,t)\,dx + b'(t)f(b(t),t) - a'(t)f(a(t),t)$$

- It's really three effects added together: (1) how the integrand itself changes with $t$, integrated over the fixed-shape interval; (2) the "gain" from the upper limit sliding outward at rate $b'(t)$; (3) the "loss" from the lower limit sliding at rate $a'(t)$.
- It's the two-limits generalization of the Fundamental Theorem of Calculus, $\frac{d}{dt}\int_a^t f(x)\,dx = f(t)$, which is the special case where $a$ is constant, $b(t)=t$, and $f$ doesn't depend on $t$.
- **Worked example (13.8 #1e):** compute $\dfrac{d^2}{dx^2}\displaystyle\int_x^{2x} \ln(u^2+x^2)\,du$.
- Here the roles are relabeled: the outer variable is $x$ (not $t$), so $a(x)=x$, $b(x)=2x$, and $f(u,x) = \ln(u^2+x^2)$ with $f_x = \dfrac{2x}{u^2+x^2}$.
- First derivative: $\dfrac{d}{dx}\int_x^{2x}\ln(u^2+x^2)\,du = 2\tan^{-1}2 - \dfrac{\pi}{2} + \ln\dfrac{25}{2} + 2\ln x$ — note everything except the $2\ln x$ term is a constant, since the boundary terms evaluate to fixed numbers once you plug in.
- Second derivative: since only $2\ln x$ survives differentiation, $\dfrac{d^2}{dx^2}\int_x^{2x}\ln(u^2+x^2)\,du = \dfrac{2}{x}$ — the whole "hard" first application of Leibniz collapses to a one-line derivative on the second pass.
--- 
#### Solving Examples

- Example 13.8: Leibniz Rule
	- $$
\begin{gather}
\text{Compute } \frac{d^2}{dx^2}\int^{2x}_{x}\ln(u^2+x^2)du \\
\text{We set } f(u, x) = \ln(u^2+x_{2}), \text{ so that } f_{x}=\frac{2x}{u^2+x^2} \\
f_{x} = \frac{u'}{u}, \text{ where } u = u^2+x^2 \\
\text{Apply Leibniz rule shown earlier} \\
\int^{2x}_{x}f_{x}(u, x)du + (2x)'_{x}f(2x, x) -(x)'_{x}f(x, x) \\
\text{Now you just need to perform simple substitutions } \\
f_x(u, x) \to \frac{2x}{u^2+x^2} \\
f(2x, x) \to \ln(4x^2+x^2) = \ln(5x^2) \\
f(x,x) \to \ln(x^2+x^2) = \ln(2x^2) \\
= \int^{2x}_{x} \frac{2x}{u^2+x^2}du+2*\ln(5x^2)-1*\ln(2x^2)
\end{gather}
$$
	- Now is where things get a little complicated
	- Simplifying the above expression requires two parts: evaluating the integral with respect to u and log simplification
	- $$
\begin{gather}
v=\frac{u}{x}, dv=\left( \frac{u}{x} \right)'du = \frac{1}{x}du \\
du = x*dv \\
\int^{2x}_{x} \frac{2x}{v^2x^2+x^2}xdv \\
\text{By simplification: }2\int \frac{1}{v^2+1}dv \\
\text{By the integration formula sheet: } \\
2\int \frac{1}{v^2+1}dv = 2\arctan\left( \frac{u}{x} \right) + C \\
\text{Next, apply log rules to simplify} \\
2\ln(5x^2) = 2\ln(5)+2\ln(x^2), \text{by: } \log_{c}(ab)=\log_{c}(a)+\log_{c}(b) \\
= 2\ln(5)+4\ln(x), \text{by: } \log_{a}(x^b) = b*\log_{a}(x) \\
\text{Evaluate prior integral between ranges 2x and x} \\

\end{gather}
$$
	- Note: the full integration for 1/v^2+1 is a little complicated, but can be followed step-by-step in [this video](https://www.youtube.com/watch?v=II7Rvv9oDsg)
	- 


## Questions/Gaps/Concerns



## Follow-up 

*actions items to follow-up on (e.g., watch video, re-read notes, hw)*



## References

*link to other notes, attachments, or actual lecture slides*

- [[Lec0909_2026.pdf]]
- -[[11 - Integration Formulas.pdf]]