2026-03-05 11:04

Course: #cis530 

## Big Ideas


## Key Concepts
- [[Decision Trees]]

## Notes
- Entropy is another way of quantifying purity
	- Where $K$ is the number of classes (usually 2)
	- $Entropy = -\Sigma_{i=1}^{K}p_{i}*\log(p_{i})$
	- Base 2 --> unit of entropy is bits
	- Base e --> unit of entropy is nats
	- Again, you take the weighted average
	- Lower is still better (range is from 0 to 1 ONLY for binary)
- Both Entropy and Gini maximize when class 1's probability is 0.5
	- Gini --> 0.5
	- Entropy --> 1.0
	- ONLY for binary classification
- They minimize when the probability for class 1 is 0 or 1
	- 0 in both cases
- Steps to apply Gini index to numerical data:
	- Sort by age
	- Calculate averages between each group of 2 ages to form average ages
	- Check Gini index for each average age and choose the lowest Gini index as the root node
		- Example: Age < 15 as the root
- For pure leaf nodes --> no need to split further
- For impure nodes --> split further and recalculate Gini index
- Overfitting is a concern in decision trees
	- Two methods to prevent: pruning (remove parts of the tree) and putting limits on how trees grow (reject when people < 3)
- Decision boundaries
	- Border line between two neighboring regions of different classes
	- 2d space --> just a line
	- 3d space --> a plane
- Generalization --> good performance on new, unseen data, indicates model has actually learned the underlying patterns in the data
- Overfitting --> model just memorizes the training data

| Model Behavior      | Training Accuracy | Testing Accuracy | What happened?              |
| ------------------- | ----------------- | ---------------- | --------------------------- |
| Underfitting        | Low               | Low              | Hasn't learned enough       |
| Overfitting         | High              | Low              | Memorized Training Data     |
| Good Generalization | High              | High             | Learned meaningful patterns |
- Overfitting reasons
	- An overfit decision boundary may fit to extreme outliers
	- Lack of data points related to a particular class
- Pruning: reduce the number of leaves in a decision tree to simplify the model
	- Based on Tree Score $= \text{Total Gini Index} + \alpha * \text{number of leaves}$
	- Choose tree with lowest tree score
	- Gini index increases as number of leaves decreases
	- To solve for $\alpha$ compute inequalities for each candidate tree


## Questions/Gaps/Concerns



## Follow-up 




## References

