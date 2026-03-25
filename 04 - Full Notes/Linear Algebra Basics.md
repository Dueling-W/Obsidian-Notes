
2026-02-11 08:15

Tags: [[linear algebra]] [[data science]]

# Linear Algebra Basics

### General Basics
- A column vector $v \in R^{n x 1}$ 
$$
v = \begin{bmatrix}
v_{1} \\
v_{2} \\
\vdots \\
v_{{n}}
\end{bmatrix}
$$
- A row vector $v^{T} \in R^{1 x n}$
$$
v^T = \begin{bmatrix}
v_{1} & v_{2} & \dots & v_{n}
\end{bmatrix}
$$
- Vectors are simply an offset in 2D or 3D space, and points are just vectors from the origin (0, 0)
- A **matrix** $A \in R^{mxn}$ is an array of numbers with size of m by n columns
$$
A = \begin{bmatrix}
a_{11} & a_{12} & a_{13} & \dots & a_{1n} \\
a_{21} & a_{22} & a_{23} & \dots & a_{2n} \\
\vdots &  &  & & \vdots \\
a_{m1} & a_{{m2}} & a_{m3} & \dots & a_{{mn}}
\end{bmatrix}
$$
- If m = n, then A is a square matrix
- **Tensor** is an array of numbers that can have 0 or more dimensions
	- 0-D --> scalar
	- 1-D --> vector
	- 2-D --> matrix
	- or more

---
### Basic Matrix Operations
- **Addition**
$$
\begin{bmatrix}
a & b \\
c & d
\end{bmatrix}
+
\begin{bmatrix}
1 & 2 \\
3 & 4
\end{bmatrix}
=
\begin{bmatrix}
a+1 & b+2 \\
c+3 & d+4
\end{bmatrix}
$$
	- Can only add a matrix with matching dimensions or a scalar
- **Scaling**
$$
\begin{bmatrix}
a & b \\
c & d
\end{bmatrix}
\times 3 = 
\begin{bmatrix}
3a & 3b \\
3c & 3d
\end{bmatrix}
$$
- **Inner product (dot product) of vectors**
	- Note: x * y is also |x||y|cos(the angle between x and y)
$$
x^Ty = \begin{bmatrix}
x_{1} & \dots & x_{n}
\end{bmatrix}
\begin{bmatrix}
y_{1} \\
\vdots \\
y_{n}
\end{bmatrix}
= \sum_{i=1}^{n}x_{{i}}y_{i}
$$
![[linear_algebra_1.png]]

- **Transpose** - flip the matrix so row 1 becomes column 1
$$
\begin{bmatrix}
0 & 1 \\
2 & 3 \\
4 & 5
\end{bmatrix}^T
= \begin{bmatrix}
0 & 2 & 4 \\
1 & 3 & 5
\end{bmatrix}
$$
	- A useful identity with transpose:
	- $(ABC)^T = C^TB^TA^T$

- **Determinant**
	- det(A) returns a scalar (singular value)
	- Represents the area (or volume) described by the vectors in the rows of the matrix (from the origin)![[lin_algebra_2.png]]
	- For $A = \begin{bmatrix}a & b \\ c & d\end{bmatrix}$ det(A) = ad - bc
	- Additional properties
		- det(AB) = det(BA)
		- $\det(A^{-1}) = \frac{1}{\det(A)}$
		- $\det(A^T) = \det(A)$
		- $\det(A) = 0 \leftrightarrow \text{A is singular}$

- **Trace**
	- $tr(A) = \text{sum of diagonal elements}$
	- $tr(\begin{bmatrix}1 & 3 \\ 5 & 7\end{bmatrix}) = 1 +7 = 8$
	- Additional properties
		- Invariant to a lot of transformation
		- $tr(AB) = tr(BA)$
		- $tr(A+B) = tr(A) + tr(B)$

- Identity matrix (I)
	- $\begin{bmatrix}1 & 0 & 0 \\ 0 & 1 & 0 \\ 0 & 0 & 1\end{bmatrix}$
	- I x \[another matrix] = \[that matrix]

- Diagonal matrix
	- $\begin{bmatrix}3 & 0 & 0 \\ 0 & 7 & 0 \\ 0 & 0 & 2.5\end{bmatrix}$
	- A diagonal x \[another matrix] scales the rows of that matrix

- Symmetric matrix
	- $A^T = A$
- Skew-symmetric matrix
	- $A^T = -A$


# References
