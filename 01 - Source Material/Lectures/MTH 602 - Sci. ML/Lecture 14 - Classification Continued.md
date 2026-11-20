2026-11-02 11:09

Course: #mth602 

## Big Ideas

*quick summary of ideas - 3-5 bullet points max*

## Key Concepts

*place links to full notes here*

## Notes
- **Simple decision boundary example**
	- *Problem set-up*
		- ![[Pasted image 20261110133442.png]]
		- $x$ is a scalar random variable for a person's height
			- Classes = {baby, adult}
	- *Probabilistic set-up*
		- Output $\vec{p} \in \mathbb{R}^2$
		- $\vec{p} = (p_{\text{baby}}, p_{\text{adult}})$
		- Example: $(0.99, .01)$
	- *Discrimination set-up*
		- Set a threshold $H^*$, where possible outputs are:
			- $$
\text{Output}: \{\begin{pmatrix}
1 \\
0
\end{pmatrix}, \begin{pmatrix}
0 \\
1
\end{pmatrix}\}
$$
		- $$
\begin{gather}
Classifier(X) = \\
\begin{cases}
0 & x \leq H^* \\
1 & x>H^*
\end{cases}
\end{gather}
$$
	- *Linear discriminator*
		- Use a linear discriminator function as the book does (5.1)
		- $$
\begin{gather}
y(x) = x-H^* \\
\text{baby if } \quad y\leq 0 \\
\text{adult if} \quad y > 0
\end{gather}
$$
- **Decision boundaries**
	- *Expand to K=2 classes*
		- $\vec{x} \in \mathbb{R}^D$, partition $\mathbb{R}^D$ using a D-1 dimensional hyperplane
			- This approach is called a linear discriminant
			- E.g., if 1 dimensional space (points drawn), then the discriminator is 1-1 = 0, which is just a singular point
		- Always D-1 dimensions --> 2-D (x,y) we get a line
	- *Linear discriminant function*
		- $$
y(\vec{x}) = \vec{w}^T \vec{x} + w_{0} = \langle \vec{w}, \vec{x} \rangle + w_{0}
$$
			- First term --> vector weights
		- $w_{0}$ --> offset from boundary 
	- *Intuition for $\vec{w}, w_{0}$*
		- Let $\omega_{0} = 0$ (special case)
			- $$
y(\vec{x}) = \vec{\omega}^T \vec{x}
$$
		- $\vec{x} = 0$ is on the surface, which means the surface goes through the origin
			- ![[Pasted image 20261110134933.png|477]]
		- If $\vec{x}_{B}$ on surface then:
			- $$
\begin{gather}
\vec{\omega}^T \vec{x} = <\vec{\omega},\vec{x}> = 0  \\
\implies \vec{\omega} \text{ is perpendicular to surface}
\end{gather}
$$
		- General case ($\omega_{0} \neq 0$): take any two points $\vec{x}_{A}, \vec{x}_{B}$ on the surface
			- $$
\begin{gather}
\vec{\omega}^T \vec{x}_{A} + \omega_{0} = 0 = \vec{\omega}^T \vec{x}_{B} + \omega_{0} \\
\implies \vec{\omega}^T (\vec{x}_{A} - \vec{x}_{B}) = 0
\end{gather}
$$
			- $\vec{x}_{A} - \vec{x}_{B}$ lies along the surface, so $\vec{\omega}$ is perpendicular to the surface for any $\omega_{0}$
		- Surface normal is defined by: 
			- $$
\hat{\omega} = \frac{\vec{\omega}}{\|\vec{\omega}\|_{2}}
$$
			- $\vec{\omega}$ determines the orientation of the surface
		- ![[Pasted image 20261110135651.png]]
		- Plane's distance from origin controlled by $\omega_{0}$
			- $$
\begin{aligned}
y(\vec{x_{B}}) &= \vec{\omega}^T \vec{x_{B}} + \omega_{0} = 0 \\
\vec{\omega}^T \vec{x_{B}} &= -\omega_{0} \\
\text{Distance } &= \frac{\vec{\omega}^T \vec{x}_{B}}{\|\vec{\omega}\|_{2}} = -\frac{\omega_{0}}{\|\vec{\omega}\|_{2}}
\end{aligned}
$$
			- Formula for signed distance based on surface orientation with $\hat{\omega}$
				- $$
\frac{y(x)}{\|\omega\|_{2}}
$$
			- The above formula tells you if you are above or below the decision surface, therefore: 
				- $$
y(\vec{x}) =
\begin{cases}
\text{Class 1}  & y \geq 0 \\
\text{Class 2} & y < 0
\end{cases}
$$
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
	- *Example using signal/noise detection*
		- ![[Pasted image 20261110141703.png|371]]
		- Every ROC curve passes through two points:
			- (0, 0) --> call nothing a signal
			- (1, 1) --> call everything a signal
		- Coin flip classifier predicts signal 50% of the time and no-signal 50% of the time 
	- Area Under Curve (AUC) --> tries to capture threshold independent model performance




## Questions/Gaps/Concerns



## Follow-up 

*actions items to follow-up on (e.g., watch video, re-read notes, hw)*



## References

*link to other notes, attachments, or actual lecture slides*
