2026-03-12 11:09

Course: #cis530

## Big Ideas


## Key Concepts


## Notes
- In-class exercise
	- If P(image = Lion) > 0.9 then it is Lion, else Tiger

| True Label | Predicited | Probabilities | Predicted Label |
| ---------- | ---------- | ------------- | --------------- |
|            | Lion       | Tiger         |                 |
| Lion       | 0.8        | 0.2           | Tiger           |
| Lion       | 0.7        | 0.3           | Tiger           |
| Tiger      | 0.5        | 0.5           | Tiger           |
| Lion       | 0.2        | 0.8           | Tiger           |
| Tiger      | 0.1        | 0.9           | Tiger           |
| Lion       | 0.99       | 0.01          | Lion            |
| Tiger      | 0.6        | 0.4           | Tiger           |
| Lion       | 0.8        | 0.2           | Tiger           |
- Confusion Matrix:

|                            | Actually Positive (Lion) | Actually Negative (Tiger) |
| -------------------------- | ------------------------ | ------------------------- |
| Predicted Positive (Lion)  | 1                        | 0                         |
| Predicted Negative (Tiger) | 4                        | 3                         |
- Accuracy:
	- $\frac{\text{Correct}}{\text{Total}}$
	- 4/8 = 50%
- Precision:
	- $\frac{\text{True Positives}}{\text{True Positives} + \text{False Positives}}$
	- Divide by total positive predictions
	- 1
	- No false positives
- Recall (sensitivity):
	- $\frac{\text{True Positives}}{\text{False Negatives} + \text{True Positives}}$
	- Basically divided by total positive samples
	- 1/5
	- 4 total false negatives

---
- Class imbalance problems
	- Option 1 --> modify an optimization criterion by using a cost sensitive matrix
	- Option 2 --> balance the class distribution (random under/over sampling)
- Small sample sizes can introduce bias/variance
- Higher sample sizes can make a more consistent model
- Specificity (for the negative class)
	- $Specificity = \frac{TN}{TN + FP}$
	- Correct negative predictions divided by total negative samples
- ROC (Receiver Operating Characteristic)
	- Trade-off between positive hits and false alarms
	- TPR (true positive rate) y-axis vs. FPR (false positive rate) x-axis
	- Plot true positive rate (recall) against false positive rate
	- $FPR = \frac{FP}{FP + TN}$
	- There is also a diagonal line, this represents a random model, guessing 50/50
	- Same concept as area under the curve for picking best model
- ROC outcomes
	- (FPR, TPR)
	- (0, 0) --> everything is negative class
	- (0, 1) --> ideal
	- (1, 1) --> everything is positive class
- ROC not ideal for really unbalanced datasets
	- Precision-recall is better for unbalanced datasets
---
- Idea: quantify how close/similar two things are
	- Ex: find similar items for two customers
	- Solve these problems we need a definition of similarity, or distance
- Similarity is just a numerical measure of how alike two data objects are
	- Range is often [0,1], sometimes [-1,1]
	- Ideally want similarity to max at 1 and have a property of similarity
- Jaccard Similarity
	- Size of their intersection divided by the size of their union 
	- Imagine you have two sets:
		- 3 in the intersection
		- 8 in union (total)
		- So Jaccard is just 3/8
	- If Jaccard = 1, just the same set
	- If 0, no shared objects between the two sets
	- Its also symmetric, which is good
- Similarity between vectors
	- Can represent a document as a vector
		- 1 dimension is a word, while the other dimension is the number of occurrences of that word
- Cosine similarity 
	- Sim(X,Y) = cos(X, Y)
	- Minimizes at 0 when the angle is 90
	- Maximizes at 1 when the angle is 0 (same vector)
	- Uses dot product formula

---
- Distance: four properties to satisfy (refer to slides)
	- E.g., should all be positive
- $L_{p}$ norms or Minkowski distance:
	- $L_{p}(x,y) = (|x_{1}-y_{1}|^p + \dots+|x_{d} - y_{d}|^p)^{1/p}$
- L2 norm is the same thing as Eulidean distance
- L1 norm is the Manhattan distance
- $L_{\infty}$ is the maximum of all distances between x and y points
	- So it ends up being a singular value just like the rest of the distances
- Can convert similarities into distances by just do 1-similarity
- Hamming distance: just the number of positions in which bit-vectors differ
	- Lower --> more similar 
	- Higher --> less similar 
	- Example:
		- x = (married, low income, cheat), y = (single, low income, not cheat), d(x,y) = 2
- Edit distance used for distance between two strings
	- Number of deletions or insertions to convert one string into another
- 

## Questions/Gaps/Concerns


## Follow-up 
- Review example of cosine similarity and make sure the math make sense.



## References

