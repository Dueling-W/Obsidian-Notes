2026-09-02 10:57

Course: #eas501 

## Big Ideas

*quick summary of ideas - 3-5 bullet points max*

## Key Concepts

*place links to full notes here*
- [[Differential Calculus]]
## Notes
- Went over syllabus first, shown below

![[syllabus_eas501.pdf]]

- The take-home project will be given during the last week of school
- No final exam for this class
- There will be two homework assignments throughout the year

--- 

- **Preliminaries (13.2)**: For vectors $x, x' \in R^n$, the Euclidean norm is $|x' - x| = \sqrt{\Sigma_{i}(x'_{i} - x_{i})^2}$, and continuity at $x_{0}$ means $\lim_{ x \to x_{0}}f(x) = f(x_{0})$
	- Continuity rules:
		1. Must be defined at that point, $f(a) \text{ is defined}$
		2. Limit must exist at the point, $\lim_{ x \to a }f(x)$ exists
		3. Value of the function at that point must equal the value of the limit at that point
			1. $\lim_{ x \to a }f(x) = f(a)$
- **Partial derivatives (13.3)**: consider a two-dimensional function $f(x, y)$, and a fixed point $(x_{0}, y_{0})$
	- The following formulas shows how the different partials are actually computed
	- In $f_{x}$, the variable $y$ is fixed; reverse for $f_{y}$
$$
f_{x}(x_{0}, y_{0}) = \frac{ \partial f }{ \partial x }(x_{0}, y_{0}) = \lim_{ \Delta x \to 0 } \frac{f(x_{0} + \Delta x, y_{0})-f(x_{0}, y_{0})}{\Delta x}  
$$
$$
f_{y}(x_{0}, y_{0}) = \frac{ \partial f }{ \partial y }(x_{0}, y_{0}) = \lim_{ \Delta y \to 0 } \frac{f(x_{0}, y_{0} + \Delta y) - f(x_{0}, y_{0})}{\Delta y}
$$
- Further partials can be defined by iterating:
	- $f_{xx} = \frac{ \partial  }{ \partial x }(f_{x})$, $f_{xy} = \frac{ \partial  }{ \partial y }(f_{x})$, and so on
- **Mixed partials aren't automatically equal**: $f(x, y) = \frac{xy(x^2-y^2)}{x^2+y^2}$ (and 0 at the origin), gives $f_{xy}(0,0) = -1\neq 1=f_{yx}(0,0)$
	- Warning/proof that order of differentiation can matter
- Clairaut's theorem (Them 13.3.1): if $f_{x}, f_{y}, f_{xy}, f_{yx}$ are continuous near $(x_{0}, y_{0})$, then $f_{xy}(x_{0}, y_{0}) = f_{yx}(x_{0}, y_{0})$
- **Chain rule (13.4):** generalizes $\frac{dF}{dt} = \frac{df}{dx} \frac{dx}{dt}$ to multiple variables: if $F(t) = f(x_{1}(t), \dots,x_{n}(t))$, then
$$
\frac{dF}{dt} = \Sigma_{i=1}^n\frac{ \partial f }{ \partial x_{i}} \frac{dx_{i}}{dt} 
$$
- **Taylor's formula & MVT (13.5):** single-variable Taylor expansion with Lagrange/integral remainder extends to 2-D:
$$
f(x, y) \approx f(a,b) + f_{x}(a,b)(x-a)+f_{y}(a,b)(y-b)+\frac{1}{2!}[f_{xx}(x-a)^2+2f_{xy}(x-a)(y-b)+f_{yy}(y-b)^2+\dots]
$$
	- Refer to worked example by bounding the error of the degree-3 Taylor polynomial for sin x on [0, 0.5]
- Implicit function theorem & Jacobians (13.6): single-variable version needs $f_{y}(x_{0}, y_{0}) \neq 0$ to guarantee $y(x)$ exists locally; the multivariable version needs the Jacobian $J = [\partial f_{i}/\partial u_{j}]$ to have $\det J \neq 0$ at the point.
	- Worked example in slides
---
**Proving Examples from Slides**
- $$
f(x, y) = 
\begin{cases} 
\frac{xy(x^2-y^2)}{x^2+y^2}, & \text{if } (x, y) \neq (0, 0) \\ 
0, & \text{if } (x, y) = (0, 0) 
\end{cases}
$$


---
- Multivariable calculus  examples - per [this video](https://www.youtube.com/watch?v=JAf_aSIJryg)
	- $$
\begin{gather} \\
\text{Example 1: Natural Log} \\
f(x,y) = \ln(x^2+y^2) \\
\frac{d}{dx}[\ln u] = \frac{u'}{u}, \text{application of chain rule} \\
f_{x} = \frac{2x+0}{x^2+y^2} = \frac{2x}{x^2+y^2} \\
f_{y} = \frac{2y}{x^2+y^2}
\end{gather}
$$
	- $$
\begin{gather}
\text{Example 2: Square Root} \\
f(x,y) = \sqrt{x^2+y^2} = [x^2+y^2]^\left( \frac{1}{2} \right), \text{rewrite} \\
f_{x} = \frac{1}{2}[x^2+y^2]^\left( -\frac{1}{2} \right)[2x+0], \text{application of chain rule} \\
f_{x} = \frac{x}{\sqrt{x^2+y^2 }} \\
f_{y} = \frac{y}{\sqrt{ x^2+y^2 }}
\end{gather}
$$
	- $$
\begin{gather}
\text{Example 3: Evaluating at a Point} \\
\text{Evaluate fx and fy at the point (1,2)} \\
f(x,y) = 2x^3y^2+5y^3+4x^2 \\
f_{x} = 6x^2y^2+8x  \\
= 6(1)^2(2)^2+8(1) \\
= 24 + 8 = 32 \\
f_{y} = 4x^3y+15y^2 \\
= 4(1)^3(2)+15(2)^2 \\
= 8 + 60 = 68
\end{gather}
$$
	- Can only apply quotient rule if variable is present in both numerator and denominator, otherwise use power rule
	- If problem says "find slope in the x and y directions" --> that means finding the partial derivatives 
	- $$
\begin{gather} \\
\text{Example 4: Partial Derivatives with Three Variables } \\
f(x,y,z) = x^5y^2z^4 \\
f_{x} = 5x^4y^2z^4 \\
f_{y} = x^52yz^4 \\
f_{z} = x^5y^2(4z^3)
\end{gather} \\
$$
	- Higher order derivatives visualized:
		- ![[Pasted image 20260908113243.png]]
	- $$
\begin{gather}
\text{Example 5: Higher Order Derivatives} \\
f(x, y, z) = x^3+4x^5y^3+5y^4 \\
Find f_{xx}, f_{xy}, f_{yx}, f_{yy} \\
f_{x} = 3x^2+20x^4y^3 \\
f_{xx} = 6x+80x^3y^3 \\
f_{xy} = 0 + 20x^4(3y^2) = 60x^4y^2 \\
\text{Other derivatives found in a similar manner}
\end{gather}
$$
	- If the function is continuous, then the mixed partials are equal (as shown in the slides)
		- This also applies to third-order derivatives, such as $f_{xyz} = f_{yzx} = \dots$
	- 





## Questions/Gaps/Concerns



## Follow-up 

*actions items to follow-up on (e.g., watch video, re-read notes, hw)*



## References

![[Derivatives Formula Sheet.pdf]]

*link to other notes, attachments, or actual lecture slides*

- Syllabus: [[syllabus_eas501.pdf]]
- Lecture Slides: [[Lec0902_2026.pdf]]
- Derivative Formula Sheet: [[Derivatives Formula Sheet.pdf]]