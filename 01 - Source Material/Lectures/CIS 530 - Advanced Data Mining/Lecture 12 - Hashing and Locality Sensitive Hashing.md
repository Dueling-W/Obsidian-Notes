2026-03-31 11:05

Course: #cis530 

## Big Ideas


## Key Concepts


## Notes
- Big categories: user-to-user filtering and item-to-item filtering
	- Called "collaborative filtering"
	- Find similar users based on a metric
	- For item s, find other similar items
- In practice, item-item usually works better than user-user
	- One benefit: more stable due to less items
- Ratings is a bit better than a content-based approach
	- Don't need to find all the attributes for ratings-based like you have to for content-based
- Pros/cons of collaborative filtering
	- Works for any kind of item (no feature selection)
	- New user and new item problem of course
	- Sparsity of rating matrix
		- Possible solution: cluster-based smoothing where you fill in the average in the given cluster
- Options for document comparison
	- Checking a set of characters (useless, all documents will contain all letters A-Z (probably))
	- Pairwise comparison between words (computational problems and just checking words lacks a lot of context)
		- Computation: $O(N^2) \text{ using naive}$
		- Need more advanced techniques (hashing) to get $O(N)$
- Big-picture workflow
	- Set of strings of length k that appear in the document 
	- Minhashing (signatures): short integer vectors from the shingles that represents the sets and reflect their similarity
	- Locality-sensitive hashing: reducing the number of pairs of documents that need to be compared
- Shingles
	- Sequence as k-tokens (can be characters or words)
	- Example: document D1 = abcab where k =2
		- Set of 2-shingles: $S(D_{1}) = {ab, bc, ca}$
		- Respect order and don't take them twice (usually), bag (multiset) is where you count ab twice
	- Need to carefully pick k
		- k = 1 (all the characters)
		- k = 5 (OK for short documents)
		- k = 10 (better for long documents)
- Compression
	- Hash shingles to (say) 4 bytes
	- Represent a doc by the set of has values
	- Example: hash shingles to 64-bit integers
- Document similarity: Jaccard similarity of the sets of shingles (the hashed shingles)
- Now, we can go from the set of hashed shingles (say 4 bytes per shingle) into a signature
	- This signature will be much smaller and the similarity of the signatures is (almost) the same as the "similarity" of the previously hashed shingles
	- Slight problem: some false negatives and false positives
- 

## Questions/Gaps/Concerns



## Follow-up 




## References

