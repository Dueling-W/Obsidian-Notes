2026-04-14 11:37

Course: #cis530

## Big Ideas
- Dimensionality reduction is reducing the number of features in the data to improving efficiency and model performance
- 

## Key Concepts
- 

## Notes
- Dimensions increase --> sparse, harder to analyze, and less meaningful for models
	- Also, higher overfitting chance due to many features being often correlated
	- Called the Curse of Dimensionality 
- Dimensionality reduction --> reducing number of features in data while having as much variability in the data as possible
	- Dimensionality reduction is good for removing noise/irrelevant features, preventing overfitting, and improving model performance
- Two categories:
	- Linear Methods: PCA (Principal Component Analysis) and LDA (Linear Discriminant Analysis)
	- Nonlinear Methods: Locally Linear Embedding
- What is PCA?
	- Finds the largest variations directions and is computed by finding the Eigenvectors of the covariance matrix of the data
	- Un-supervised learning
- What is LDA?
	- Considers the label information which maximizes the distance between classes, and minimizes the distance within a class
- PCA example: collapsing two features (height/weight) into a singular line (linear) on which we can project all the points
- PCA step-by-step
	1) Center the data by finding the mean for each feature, plot that point as an (x,y) and then shift that point to the origin
		1) Subtract each point by the mean to shift the points relative to the new origin
	2) Finding the best fitting line
		1) Minimize the sum of the distance from the points to the line
		2) 

## Questions/Gaps/Concerns



## Follow-up 




## References

