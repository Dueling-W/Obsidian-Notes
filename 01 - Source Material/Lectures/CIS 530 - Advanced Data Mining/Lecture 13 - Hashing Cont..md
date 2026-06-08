2026-04-02 11:08

Course: #cis530

## Big Ideas


## Key Concepts


## Notes
- Exercise on slide 33
	- Pretty simple, calculate unique shingles, make a one-hot-matrix (consists of 0s and 1s)
	- Then calculate Jaccard similarity (remember it is the intersection over the union between the two sets)
		- So ignore the shingles where both documents are 0
- Minhashing
	- Pick random permutation of rows (the shingles)
	- Define "hash" function
		- h(S) = the index of the first row (in the permuted order) in which column S has 1
		- Say the first "1" occurs in index 3, so the signature for that set would just be 3
	- \# of signatures depends on value of k (k=100 is 100 signatures)
- Based on the number of signatures, you get a signature matrix
	- Now, each set/document has its own vector based on the different hashes
	- So, if you had k = 3, then you would have something like:
		- $Sig(S_{2}) = [2, 1, 1]$
- Two properties of the signature matrix/minhashing
	- Compress (save space over one-hot matrix)
	- Still be able to get the similarity 
- Key idea: probability that h(X) = h(Y) on a given row is just intersection/union
	- Ignore rows that aren't union (they don't matter)
- Similarity of signatures is the fraction of the hash functions where they agree
	- More signatures --> better approximation
	- Zero similarity is always preserved for the signatures
- Still some problems with min-hash signatures
	- Possible solution: apply a hash function to the rows instead
	- Value of has function is the position of the row in the new order
- 

## Questions/Gaps/Concerns



## Follow-up 




## References

