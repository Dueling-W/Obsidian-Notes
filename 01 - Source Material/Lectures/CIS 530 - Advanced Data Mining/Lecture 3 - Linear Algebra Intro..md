2026-02-05 11:05

Course: #cis530 

## Big Ideas
- Numpy > Standard Python
- Matrix operations: subtraction, addition, scaling, multiplication
	- Special operations: determinate, trace
- Special matrices: identity matrix, diagonal matrix, symmetric matrix, skew-symmetric matrix

## Key Concepts*
- Linear algebra basics 

## Notes
- Use numpy (Python lib) or matlab for this course
- Determinate is a useful scalar property, represents area of a parallelogram 
- Trace is the sum of the diagonal elements
- Special matrices:
	- Identity matrix - square matrix with 1's along the diagonal and 0's elsewhere
	- Diagonal matrix: square matrix with numbers along diagonal, 0's elsewhere
		- Use case: scaling
	- Symmetric matrix: A-transpose = A
	- Skew-symmetric: A-transpose equal to -A
- If det(A) = 0, then A is singular or invertible
	- Meaning you cannot inverse the matrix
- Useful to look into inverse computations
- Can use mldivide to directly solve for X in AX=B by typing A\B
	- np.linalg.lstq is the equivalent in Python
- Linear dependency: if we can represent a vector as a linear combination of the other vectors, then v1 is linearly dependent on the other vectors
	- If no vector is linearly dependent on the rest of the set, the set is linearly independent 
- Column/row rank
	- Maximum number of linearly independent column vectors of A
	- Same thing for rows
	- Key concept: maximum number of independent columns/rows *at a given time* 
		- So even though multiple columns may be dependent
- Rank = column rank = row rank
	- Rank tells you the dimensions of the output for transformation matrices
- Full rank: if an mxm matrix is rank m
- If rank < m, we say its "singular"


## Questions/Gaps/Concerns
- What are some of the edge cases of matrix rank and what are the exact use cases?
- Can rank go beyond 2 dimensions?


## Follow-up 
- Create linear algebra intro note
- Re-code Python/MatLab examples; investigate mldivide
- 



## References



*\*Replace with links when actual note is created
