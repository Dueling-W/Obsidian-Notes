2026-02-12 11:18

Course: #cis530

## Big Ideas
- SVD is used to decompose a matrix (factorization)
- SVD is built from singular values and eigenvectors

## Key Concepts
- Eigenvectors and Values

## Notes
- Singular value = $\sqrt{\text{eigenvalues}}$
- Goal of SVD: factorize a matrix
	- SVD = $U\Sigma V^T$
- Properties of SVD
	- Assume A is $m\times n$
	- U is $m\times m$
	- $\Sigma \text{ is } m \times n$
	- V is $n \times n$
- U and $V^T$ both contain the normalized eigen vectors in descending order, while $\Sigma$ contains the singular values on the diagonal
	- U is $AA^T$ while V is $A^TA$
	- Put everything as zero in $\Sigma$ if you run out of $\sigma$ values
- SVD is useful for image compression
	- Can represent as several low-rank (1 rank) matrices


## Questions/Gaps/Concerns



## Follow-up 
- View helpful video from slides showing low rank approximation of images



## References

