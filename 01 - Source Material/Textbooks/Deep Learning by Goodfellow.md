
## Chapter 1 - Introduction

**Active Notes**
- Artificial intelligence tasks --> provide features to a simple ML algorithm
- Representation learning --> learned representations instead of hand-designed representations
	- Learned often results in much better performance
	- Goal is to discover a useful set of features
	- Example: autoencoder (combination of an encoder function and a decoder function)
- Feedforward deep network (multilayer perceptron)
	- Maps some set of input values to output values
- ![[Pasted image 20260729094350.png]]
- ![[Pasted image 20260729094702.png]]
- Deep learning is a kind of machine learning that achieves great power and flexibility by representing the world as a nested hierarchy of concepts
	- Each of these concepts is defined in relation to simpler concepts
- Famous limitation of linear models --> cannot learn the XOR function

**Chapter Summary**
- AI is the overall field attempting to model human intelligence
- Deep learning is a subset of machine learning that achieves greater power and flexibility
	- It does this by enabling the computer to build complex concepts out of simpler concepts
- Deep learning is an old field dating back to the 1950s
	- Achieved recent success due to better hardware, larger datasets, and increasing model size


### Chapter 2 - Linear Algebra

**Active Notes**
- Most concepts were covered in my deep learning course, so won't go into extreme detail
	- The basic definitions (scalars, vectors) and multiplying matricies are covered in enough detail in [[Linear Algebra Basics]]
- **Norms** --> a way of measuring the size of a vector
	- Basic $L^p$ norm given by:
		- $||x||_{p} = (\sum_{i}|x_{i}|^p)^\frac{1}{p}$
	- L2 norm with p = 2 is Euclidean norm, which is the Euclidean distance from the origin to the point identified by x
	- Dot product is: $|x||y|\cos(\theta)$
- Special matricies
	- Diagonal matrices --> mostly zeros and have nonzero entries only along the main diagonal 
		- Formal: $\text{matrix D is diagonal iff } D_{i,j} = 0 \text{ for all } i \neq j$
	- Nonsquare diagonal matrices don't have inverses
	- Symmetric matrix: $A = A^T$
- Eigendecomposition
	- Process of decomposing a matrix into a set of eigenvectors and eigenvalues
	- Eigenvector --> nonzero vector v such that multiplication by A alters only the scale of v:
		- $Av = \lambda v$
		- The scalar $\lambda$ is the eigenvalue for that eigenvector
- SVD (Singular Value Decomposition)
	- $A = UDV^T$
	- Sizes:
		- A is an $m \times n$ matrix
		- U would be a $m \times m$ matrix
		- D would be an $m \times n$ matrix
		- V would be an $n \times n$ matrix
	- U and V are both orthogonal matrices
	- D (or Sigma) is defined as a diagonal matrix
		- The elements along the diagonal of D are known as the singular values


### Chapter 3 - Probability and Information Theory

**Active Notes**
- Motivation --> machine learning deals with uncertain quantities and sometimes stochastic quantities
- Sources of uncertainty:
	- Inherent stochasticity in the system being modeled
	- Incomplete observability (e.g., Monty Hall problem)
	- Incomplete modeling (such as simplifying a continuous space into a discrete one - discretizes)
- Frequentist probability --> related to the rates at which events occur
- Bayesian probability --> related to qualitative levels of certainty
	- Takes into context available evidence (prior)
- Random variable --> variable that can take on different values randomly
- Probability distribution --> description of how likely a random variable or set of random variables is to take on each of its possible states
	- Can be a discrete or continuous distribution
- Discrete --> use a probability mass function (PMF)
	- Probability distribution over many variables is known as a joint probability distribution: $P(\text{x} = x, \text{y} = y)$
		- Means probability that x and y take those values
	- ![[Pasted image 20260803101047.png|570]]
- Continuous random variables --> probability density function (PDF)
	- Properties of a function $p$ to be a PDF
		- The domain of $p$ must be the set of all possible states of x
		- $\forall x \in x,p(x) \geq 0$
		- $\int p(x)dx = 1$
	- The probability that $x$ lies in the interval $[a, b]$ is given by $\int_{a}^bp(x)dx$
- Conditional Probability
	- $P(\text{y} = y | \text{x} = x) = \frac{P(\text{y} = y, \text{x} = x)}{P(\text{x} = x)}$
	- So here, it is the probability that $\text{y} = y$ given $\text{x} = x$
- There is some more general theory regarding: chain rule, independence and conditional independence, expectation (refer to chapter if this information is necessary)
- Common Probability Distributions
	- Bernoulli: distribution over a single binary random variable
	- Multinoulli: distribution over a single discrete variable with $k$ different states
	- Gaussian (normal) distribution:
		- $\mu$ gives the coordinate of the central peak
		- $\sigma$ gives the standard deviation of the distribution
		- ![[Pasted image 20260803111708.png]]
		- Central limit theorem (shows that the sum of many independent random variables is approximately normally distributed)
- Logistic sigmoid:
	- $\sigma(x) = \frac{1}{1+\exp(-x)}$
	- Commonly used to produce the $\phi$ parameter of a Bernoulli (binary) distribution because its range is (0, 1)
	- ![[Pasted image 20260803113618.png]]
- Entropy and information theory:
	- Revolves around quantifying how much information is present in a signal/prediction
