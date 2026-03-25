2026-03-03 11:03

Course: #cis530 

## Big Ideas


## Key Concepts
- [[Decision Trees]]
- [[Classification Metrics]]

## Notes
- Project information
	- End-to-end system
		- Full application including an application/web browser
		- Example: facial recognition software that also includes a way to upload faces, database, etc.
	- Critical applications
		- Solving a critical application across many domains and comparing different models
	- Systematic evaluations/baselines/benchmarks
		- Compare pros and cons of different models on large, pre-defined datasets (e.g., MNIST, PIE, YaleB)
		- Focus is on comprehensive comparison using tables, curves, bars, etc.
	- Example areas
		- Visual intelligent recognition (vision project, video understanding)
		- Web and graph mining
---
- Classification learns a target function f that maps attribute set x to one of the predefined class labels y
- Descriptive vs. predictive modeling
	- Descriptive: focusing on the analysis, what is some inference from features $x$ that describes output $y$
	- Predictive: just predict the class of a previously unseen record
		- Generalization and accuracy focused
- Evaluation of classification models
	- Confusion matrix
		- Predicted vs. actual class
	- $Accuracy = \frac{\text{correct predictions}}{\text{total predictions}}$
	- $Error rate = \frac{\text{errors}}{\text{{total predictions}}}$
	- Accuracy could also be expressed as just $1-\text{errorrate}$
	- Precision, recall, F1-score
		- Help to deal with imbalanced datasets by providing more information
	- $\text{F1 Score} = 2 \times \frac{\text{Precision x Recall}}{\text{Precision + Recall}}$
- Decision tree types
	- Classification tree (predicts categorical targets values)
	- Regression tree (continuous target values)
- Decision tree basics
	- Root nodes, internal nodes, and leaf nodes are the general structure
	- And it looks like a tree
- Tree induction
	- But how to find a "good" tree for the data
	- Finding best solution is NP-hard
	- Greedy strategy
	- Many algorithms: common one in this class is the CART algorithm
- Leaf nodes which consist of mixtures of classifications --> impure
	- Pure nodes have no mixed classification (so its all Yes, No, or something else), but it is all in one category
	- Need a technical way to measure leaf purity 
- Gini index
	- First introduced way to measure leaf purity 
	- If a node has K classes (such as 2):
		- $\text{Gini Index} = 1 - \Sigma^{K}_{i=1}p_{i}^{2}$
		- where $p_{i}$ is probability on the leaf
	- Higher value --> more impure
	- Total Gini index is just the weighted average of the Gini index of the total leaf nodes from the decision
		- E.g., node "Loves YouTube" has two leafs: Yes or No
- 



## Questions/Gaps/Concerns



## Follow-up 
- Look into final course project and possibly choose a topic.
- Watch mandatory lecture on probability from missed class.



## References

