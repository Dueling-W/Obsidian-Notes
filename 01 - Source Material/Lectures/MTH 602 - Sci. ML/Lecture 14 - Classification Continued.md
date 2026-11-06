2026-11-02 11:09

Course: #mth602 

## Big Ideas

*quick summary of ideas - 3-5 bullet points max*

## Key Concepts

*place links to full notes here*

## Notes
- **Decision boundaries**
	- *Example*
		- X is a scalar random variable for height
		- Classes: {"baby", "adult"}
		- Idea is two histograms that are well separated
		- There is some point (H*) that separates the two
		- $$
\begin{gather}
Classifier(X) = \\
\begin{cases}
0 & x \leq H^* \\
1 & x>H^*
\end{cases}
\end{gather}
$$
	- *Expand to K=2 classes*
		- $\vec{x} \in \mathbb{R}^D$, partition $\mathbb{R}^D$ using a D-1 dimensional hyperplane
		- This is called the decision boundary
		- Always D-1 dimensions --> 2-D (x,y) we get a line
	- *Linear discriminant function*
		- $$
y(\vec{x}) = \vec{w}^T \vec{x} + w_{0} = \langle \vec{w}, \vec{x} \rangle + w_{0}
$$
		- First term --> vector weights
		- $w_{0}$ is offset from boundary 
		- Decision boundary = $$
\{\vec{x}_{B}: y(\vec{x}) = 0\}
$$
		- $$
y(\vec{x}) =
\begin{cases}
\text{Class 1}  & y \leq 0 \\
\text{Class 2} & y > 0
\end{cases}
$$
	- *Investigating $w_{0}$ parameter*
		- Simple case: where $w_{0} = 0$, which means the decision boundary passes through the origin
			- [insert picture of graph from scanned lecture notes]
			1. Does it go through the origin?
				1. Yes, $\vec{x} = (0, 0)$
			2. Is $\vec{\omega}$ and $\hat{\omega} = \frac{\vec{\omega}}{\|\omega\|}$ perpendicular to the boundary?
				1. Yes, but I don't know why exactly. used the angular brackets from before I think with the $y(\vec{x})$ formula
		- Now, check when $\omega_{0} \neq 0$
			- Formula becomes: $$
y(\vec{x}) = \langle \vec{w}, \vec{x} \rangle + w_{0}
$$
			- \[need to turn image into notes]
- **ROC and AUC**
	- ROC = Receiver Operating Characteristic Curve
	- x-axis: FPR (False Positive Rate)
		- $$
\frac{FP}{FP+TN}
$$
		- Where FP = False Positive and TN = True Negative
	- y-axis: TPR (True Positive Rate)
		- $$
\frac{TP}{TP+FN}
$$
		- Where FN = False Negative and TP = True Positive
		- 




## Questions/Gaps/Concerns



## Follow-up 

*actions items to follow-up on (e.g., watch video, re-read notes, hw)*



## References

*link to other notes, attachments, or actual lecture slides*
