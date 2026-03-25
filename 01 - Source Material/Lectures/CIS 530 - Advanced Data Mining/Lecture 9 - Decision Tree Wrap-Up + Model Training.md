2026-03-10 11:07

Course: #cis530

## Big Ideas
- Pruning and generalization error estimates are used to obtain high accuracy with small decision trees

## Key Concepts
- [[Decision Trees]]

## Notes
- Pessimistic approach for generalization error estimate
	- Total errors: $e'(T) = e(T) + N \times 0.5$
		- Where $N$ is the number of leaf nodes
		- This penalizes large trees
- Choosing $\alpha$
	- Tree 1: testing accuracy = 0.33
		- Range: $0 < \alpha \leq 0.214$
	- Tree 2: testing accuracy = 1
		- Range: $0.214 < \alpha \leq 0.275$
	- Tree 3: testing accuracy = 0.66
		- Range: $\alpha > 0.275$
- Decision tree summary

| **Pros**                                |
| --------------------------------------- |
| Inexpensive $O(\log_{2}(n))$ complexity |
| Exttremely fast                         |
| Easy to interpret                       |
| Accuracy strong on simple data sets     |
- Validation set strategies
	- Fixed split (split entire dataset into training, validation, and testing proportions)
		- E.g., 70% train, 15% test, 15% validation
		- Then, train the model for each hyperparameter combination $c$
	- k-fold cross validation: used when the size of the total dataset is limited
		- Imagine 75% data is training and 25% is testing
		- Divide the 75% training into five-equal 15% folds
		- Select one fold (one 15% part) and use it for validation, use the other 85% for training
		- Repeat until all folds have been a validation partition at least once
- Precision-Recall curve
	- Controls the precision/recall tradeoff
	- Precision (y-axis) vs. recall (x-axis)
	- Each point (r, p) changes with the value of threshold
		- Where threshold controls the decision threshold
		- Raising threshold --> higher precision, lower recall
		- Lowering threshold --> higher recall, lower precision


## Questions/Gaps/Concerns
- How is k-fold cross validation implemented? Are there guidelines for how many folds to generate?
- 

## Follow-up 
- Look into k-fold cross validation implementation in Python



## Reference(s)

