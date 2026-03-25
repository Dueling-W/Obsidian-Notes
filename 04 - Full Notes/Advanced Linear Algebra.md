
2026-02-17 15:54

Tags: [[linear algebra]] [[data science]]

# Advanced Linear Algebra


### Inverses and Pseudoinverses
- Given a matrix $A$, its inverse $A^{-1}$ is a matrix such that $AA^{-1}=A^{-1}A=I$
	- E.g. $\begin{bmatrix}2 & 0 \\ 0 & 3\end{bmatrix}^{-1} = \begin{bmatrix} \frac{1}{2} & 0 \\ 0 & \frac{1}{3}\end{bmatrix}$
- If $A^{-1}$ exists, then *A* is invertible or non-singular
	- Otherwise it is known as *singular* 

- Pseudo-inverses are used when trying to solve for a variable
- E.g., $AX = B$ can be turned into $AA^{-1}X = BA^{-1} \to X = A^{-1}B$
- Can run into problems with really large matrices
	- Solution: use mldivide from MatLab: X = A\B





# References
