2026-04-21 11:15

Course: #cis530

## Big Ideas


## Key Concepts
- [[LDA]]

## Notes
- LDA --> find a projection to achieve two goals
	- Make samples from same class compact
	- Make samples from different classes dispart
- To achieve the two goals, we will
	- $\text{max} \frac{w^TS_{b}w}{w^TS_{w}w}$
	- Top is maximizing the distance of the between classes and the denominator is minimizing the distance of the within class
- Helpful PDF on Canvas walks through everything step-by-step
---
- Unsupervised learning
	- Cluster: a broad category (e.g., K-means, DBSCAN, spectral clustering)
		- Also time-series is possible using a Hidden Markov Chain
	- Con: more subjective compared to supervised learning
	- Merits: often easier to find unlabeled data
- Two types of clustering:
	- Partitional (each point has their own cluster) and hierarchical (points can belong to multiple clusters, so nested clusters)
- K-means idea:
	- Most common definition uses euclidean distance, minimizing the Sum of Squares Error (SSE) function
	- $Cost(C) = \Sigma^K_{i=1}\Sigma_{x \in C_{i}}(x-u_{i})^2$
- ```
  Select K points as the initial centroids.
  repeat
	  Form K cluseters by assigning all points to the closest centroid.
	  Recompute the centroid of each cluster
  until The centroids don't change
  ```
	- The initial centroids are random
	- 
## Questions/Gaps/Concerns



## Follow-up 




## References

