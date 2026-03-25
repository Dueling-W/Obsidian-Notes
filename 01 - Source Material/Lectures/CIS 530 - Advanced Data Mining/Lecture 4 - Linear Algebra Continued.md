2026-02-10 11:05

Course: #cis530

## Big Ideas
- Vectors can be scaled/modified by special matrices (identity, scalar, off-one, orthogonal)
- If dot product of two vectors = 0 --> they are orthogonal (or perpendicular) 

## Key Concepts


## Notes
- Scalar matrix (similar to identity matrix)
	- Everything is zero and there is a value along the diagonal
	- If value >1, vector stretches
	- If between 0 and 1, vector shrinks
	- If equal to 1, no change (identity matrix)
	- If zero, everything collapses to the zero vector
- Off-One matrix (only scales a particular dimension)
- Orthogonal Matrix
	- Square matrix where the column vectors are orthogonal, i.e., perpendicular to each other
	- If two vectors are perpendicular, then the dot product is zero
	- What are they used for? --> rotation and reflection
- New vector from rotation: \[component in direction of new x axis, component in direction of new y axis]
- Multiple transformation matrices can be used: p' = R2R1Sp
	- In this example: (R2(R1(Sp)))
- Eigen vectors and eigen values
	- A non-zero vector v is called an eigenvector of A if
		- Av = sv
		- After the transformation matrix A, vector v has the same direction and is scaled by s
	- The scaler is called the eigenvalue corresponding to the vector
	- Eigenvectors can be real or complex
		- Need to solve for lamba to find out your values, but the total should be equal to n
- Rectangular matrix to symmetric matrix
	- A\*A^T results in a square symmetric matrix
	- The extra eigenvalue is always zero from the left and right symmetric matrices
- SVD: singular value decomposition 
	- Three components

## Questions/Gaps/Concerns
- What are the key components of the rotation matrix, how was it created?
- How exactly to find eigenvectors and eigenvalues?


## Follow-up 
- Look into stack exchange on rotation matrices: [Stack Exchange](https://math.stackexchange.com/questions/363652/understanding-rotation-matrices)
- Put notes into linear algebra basics note
- Refer to PDF of finding eigenvectors for a more detailed explanation



## References

