
## Chapter 1


### Summary Notes:
- 

### Active Notes:
- Examples of deep learning (pgs. 1-6)
	- Medical diagnosis (e.g., skin lesions)
		- An example of supervised learning (given labels) and classification (each input is assigned a discrete set of classes)
		- When outputs consist of one or more continuous variables --> regression problem
		- Transfer learning --> takes a large model (trained on general images) and applies it to a specialized problem (skin images)
	- Protein structure
		- Take amino acids as input --> generate 3D structure as output
	- Image synthesis
		- Unsupervised  --> images are unlabeled 
		- Generative model --> generate new output examples that differ from those used to train the model
			- But share the same statistical properties
	- Large language models
		- LLM --> build rich internal representations to capture the semantics of language
		- Autoregressive LLM --> a form of gen. AI that can generate language as output
		- Loop: take sequence of words as input --> generate next word --> generate next word
- Basic example (pgs. 6 - 12)
	- Problem setup
		- Input variable $x$, target variable $t$
			- Both variables are continuous on the real axis
		- $N = 10$ data points evenly spaced out and generated with the function $\sin(2\pi x)$ 
		- Random noise (Gaussian) was then added to each point to generate the corresponding variable $t$
		- We wish to predict a value for $t_{n}$ given a $x_{n}$
	- The randomness is present in a lot of real-world datasets
	- To start with, the book considers a simple approach based on curve fitting, using the polynomial function of the form:
	$$
y(x, w) = w_{0}+w_{1}x+w_{2}x^2+\dots+w_{M}x^M = \sum_{j=0}^Mw_{j}x^j 
$$
	- While the polynomial function $y(x, w)$ is a nonlinear function of x, it is a linear function of the coefficients w
	- Determine coefficient values --> fit polynomial to training data --> minimize an error function that measures the misfit
	- Misfit measure --> sum of the squares of the differences between the predictions $y(x_{n}, w)$ for each data point $x_{n}$ and the corresponding target $t_{n}$ given by
	- 
$$
E(w) = \frac{1}{2}\sum_{n=1}^N(y(x_{n}, w)-t_{n})^2
$$
- cont.
	- Book tested different parameters on $M$
		- 0 and 1 order polynomials --> very poor fitting
		- 3 --> overall very good
		- 9 --> fits through all the points perfectly, but is an example of *overfitting*
		- Overfitting --> good training accuracy but actually fits to the function $\sin(2\pi x)$ poorly
	- In the worked example, the coefficients have become very finely tuned to the data --> exhibiting both large negative/positive values
	- Larger datasets can also help with reducing the overfitting problem (large data set, we can afford to fit a more complex model)
- Regularization and more (pgs. 12 - 13 )
	- Simple penalty term added to the coefficients to discourage large magnitudes
	- $$
E(w) = \frac{1}{2}\sum_{n=1}^N(y(x_{n}, w)-t_{n})^2 + \frac{\lambda}{2}
||w||^2$$
	- where the coefficient $\lambda$ governs the relative importance of the regularization term compared with the sum-of-squares error
		- E.g., with $\ln \lambda$ equal to -18, the 9-th degree polynomial fits well, but with $\ln\lambda$ equal to 0 the function becomes flat
- Model selection (pgs. 14-15)
	- The quantity $\lambda$ is an example of a *hyperparameter* since we can't just simply minimize w.r.t. w and $\lambda$ since the model will just become overfit
		- Degree of polynomial ($M$) is also a hyperparameter, since minimizing will just, again, result in 0 training error and an extremely overfit model
	- Simple solution --> use a training set and a separate validation set, then select the model with the lowest error on the validation set
		- Might overfit on validation --> test set may become necessary
	- **Cross-validation** --> simple way to make use of all available data
		- ![[Figure_11.pdf]]
		- Illustrated here, each partition is used for validation and then the performance scores from the $S$ runs are then averaged
- Brief history of Machine Learning (pgs. 16-18)
	- Neural networks --> based on the neurons in the brains of humans and other mammals
	- Basic idea behind artifical neural networks:
		1. Describe the properties of a single neuron by forming a linear combination of the outputs of other neurons
		2. Transform it using a nonlinear function
	- $$
\begin{gather}
a = \sum_{t=1}^Mw_{i}x_{i} \\
y = f(a) \\
\end{gather}
$$
		- where $x_{1}, \dots, x_{M}$ represent $M$ inputs corresponding to the activities of other neurons that send connections to this neuron
		- and $w_{1}, \dots , w_{M}$ are continuous variables called weights, which represent the strengths of the associated synapses
	- Terminology:
		- quantity $a$ --> called the pre-activation
		- non-linear function $f(.)$ --> activation function
		- output y --> activation 
	- Single-layer neural network --> perceptron 
- Backpropagation (pgs.19-20)
	- Problem --> training multi-layer neural networks
	- Solution --> application of gradient based optimization methods
	- New training process for feed-forward (or multi-layer) neural networks:
		1. Initialize all parameters using a random number generator
		2. Iteratively update them using gradient-based optimization techniques
		3. Compute derivatives of the error function, done in a process known as *error backpropagation 
	- While there exist many optimization algorithms, the most common is known as stochastic gradient descent
- Deep networks (pgs. 20-22)
	- Networks with many layers of weights --> called deep neural networks
	- Massive models (parameters in the trillions) --> necessitate large datasets for good parameters values =  lots of computation
		- Of course, solution is GPUs



## Chapter 2


### Summary Notes


### Active Notes
- **Probability intro**
	- *Probability theory* provides a consistent paradigm for the quantification and manipulation of uncertainty
	- Idea of infinite trials:
		- Bent coin has 60% chance to land concave side up, 40% chance to land convex side up
		- But strictly, it is defined in the limit of an infinite number of coin flips
		- Known as the *frequentist* view of statistics
	- Use of probability as a quantification of uncertainty is the *Bayesian* perspective
		- Learn about which side is heads/tails if we are given data (a sequence of coin flips), known as *Bayesian reasoning*
		- More results --> less uncertain we are about which side of the coin is heads/tails
- **A medical screening example**
	- Concept of *false positives and false negatives* in cancer screening
		- 1% of the population has cancer
		- 3% of people who are free of cancer will test positive (false positive)
		- 10% of people who have cancer will test negative (false negative)
	- Want to answer two questions:
		1. "If we screen the population, what is the probability that someone will test positive?"
		2. "If someone receives a positive test result, what is the probability that they actually have cancer?"
	- Will come back to these questions
- **The sum and product rules**
	- *Random or stochastic variables*
		- $X$ can take any of the values $x_{i}$ where $i = 1, \dots, L$
		- $Y$ can take the values $y_{j}$ where $j = 1, \dots, M$
	- Total trials (or data points) we denote as $N$, where we sample each of the variables X and Y
		- Let the number of trials in which $X=x_{i}$ and $Y=y_{j}$ be $n_{{ij}}$
		- Let the number of trials in which $X$ takes the value $x_{i}$ (irrespective of the value that $Y$ takes) be denoted by $c_{i}$ and similarly let the number of trials in which $Y$ takes the value $y_{j}$ be denoted by $r_{j}$
	- *Joint probability*
		- $$
p(X=x_{i}, Y=y_{j}) = \frac{n_{ij}}{N}
$$
		- In words: probability that X will take on value x_i and Y will take on value y_j
	- *Marginal probability*
		- Probability that $X$ takes on the value $x_{i}$, irrespective of the value of $Y$
		- $$
P(X= x_{i}) = \frac{c_{i}}{N}
$$
		- Since $\sum_{i}c_{i} = N$, we see that:
		- $$
\sum^L_{i=1}p(X=x_{i}) = 1
$$
		- Verifying that the probabilities sum to one as required
	- *Sum rule and product rule*
		- $$
\begin{gather}
\text{sum rule} & p(X) = \sum_{Y}p(X, Y) \\
\text{product rule} & p(X, Y) = p(Y |X)p(X)
\end{gather}
$$
		- The p(Y|X) is read as "the probability of Y given X" and is known as a *conditional probability*
- **Bayes theorem**
	- Using the product rule with symmetry property, we obtain:
		- $$
p(Y|X) = \frac{p(X|Y)p(Y)}{p(X)}
$$
		- Which is called Bayes' theorem
	- The Bayes' theorem denominator can be expressed as:
		- $$
p(X) = \sum_{Y}p(X|Y)p(Y)
$$
		- This is the actual important one and the one more commonly used!!!
	- Example involving a joint distribution over two variables
		- Here we have $N=60$ datapoints
		- ![[Figure_5_a.pdf]]
			- The overall joint probability is shown in the above image
			- X can take on 9 possible values, which Y can take on 2
		- ![[Figure_5_b.pdf]]
			- Marginal distribution of Y (which simply means the probability of Y)
			- Seems like it takes on $Y=1$ more often than $Y=2$
		- ![[Figure_5_c.pdf]]
			- Marginal distribution of X (which simply means the probability of X)
			- There are 9 bars because X can take on 9 different values
			- You just sum up the rectangles 
		- ![[Figure_5_d.pdf]]
			- Final, this is the conditional distribution, saying, "what is the probability of X if Y = 1"
			- Note that there are only 7 bars because X is never 8 or 9 when Y = 1 (only happens when Y = 2)
- **Revising medical screening example**
	- Our random variable is C and it can take on two values: 0 (no cancer) or 1 (cancer)
	- Assumed probabilities:
		- $$
\begin{gather}
p(C=1) = \frac{1}{100} \\
p(C = 0) = \frac{99}{100}
\end{gather}
$$
	 - We have the probabilities from a screening test as well, if someone has cancer, 90% positive test, if they do not have cancer, the probability of a positive test is 3%:
		 - $$
\begin{gather}
p(T=1|C=1) = \frac{90}{100} \\
P(T=0|C=1) = \frac{10}{100} \\
P(T=1|C=0) = \frac{3}{100} \\
P(T=0|C=0) = \frac{97}{100}
\end{gather}
$$
		 - Note that the probabilities sum to 1 for each case
	 - Now, lets apply our sum and product rules to determine the overall probability that someone who is tested at random will have a positive test result
		 - Reminder: probability of cancer in population is 1%
		 - $$
\begin{gather}
p(X) = \sum_{Y}p(X|Y)p(Y) \qquad \text{using sum rule} \\
p(T=1) = \sum_{C}p(T=1 |C)p(C) \qquad \text{summing over cancer} \\
p(T=1)=p(T=1|C=0)p(C=0)+p(T=1|C=1)p(C=1) \\
= \frac{3}{100} \times \frac{99}{100} + \frac{90}{100} \times \frac{1}{100} \\
= \frac{387}{10,000} = 0.0387 = 3.87\%
\end{gather}
$$
		- So, if we run our cancer test at random, there is a 3.87% chance of someone testing positive, despite chance only being a 1% chance
		- You can also do the inverse: 100-3.87 = 96.13% chance of someone testing negative
	- Second question is a test is positive, what is the probability that the person has cancer?
		- $$
p(Y|X) = \frac{p(X|Y)p(Y)}{p(X)} \qquad \text{Bayes' theorem}
$$
		- $$
\begin{gather}
p(C=1 | T=1) = \frac{p(T=1 |C=1)p(C=1)}{p(T=1)} \\
\text{Know that: } p(T=1|C=1)=\frac{90}{100}, \quad p(C=1)=\frac{1}{100}, \quad p(T=1) = \frac{387}{10,000} \\
= \frac{\frac{90}{100} \times \frac{1}{100} }{\frac{387}{10,000}} \\
= \frac{90}{387} \approx 0.23 = 23\%
\end{gather}
$$
		- Conclusion: if a test is positive, there is only a 23% chance that the person actually has cancer
		- Do the inverse: 100-23 = 77% chance, meaning, there is a 77% chance the person doesn't have cancer if the test is positive
	- Overall reading of the test:
		- **Negative result:** strong evidence of no cancer for that person ($1\% \to 0.1\%$).
		- **Positive result:** not a diagnosis ($1\% \to 23\%$), but enough to justify further testing.
- **Prior, posterior, and independent variables**
	- *Prior probability*
		- Probability available *before* we observe the result of the test
	- *Posterior probability*
		- Probability obtained *after* we have observed the test result *T*
	- In our cancer example the:
		- Prior --> is the probability of having cancer being 1%
		- Posterior --> once we have observed the test being positive, we find that the posterior probability of cancer is now 23%
	- Idea of low prior
		- May seem that 23% chance seems low still, since test appears so accurate from Figure 2.3
		- Reason --> low prior probability (1%) of having cancer
			- The test itself provides strong evidence of cancer, but it needs to be combined with the prior
	- *Independent variables*
		- Def. --> if a joint distribution, $p(X, Y)$ can factorize into the marginals, $p(X)p(Y)$, then $X$ and $Y$ are said to be *independent*
			- $p(X, Y) = p(X)p(Y)$ <-- independent check
		- Example would be the successive flips of a coin
		- Using product + Bayes' rule to check:
			- $$
\begin{gather}
\text{Use that } \quad p(X,Y) = p(X)p(Y) \\
\text{Apply Bayes' rule } \quad p(Y|X) = \frac{p(X|Y)p(Y)}{p(X)} \\
\text{Note the numerator is product rule } \quad p(Y, X) = \dots \\
\text{Apply new def. of product rule } \quad p(Y|X) = \frac{p(X)p(Y)}{p(X)} \\
\text{So, } \quad p(Y|X)=p(Y)
\end{gather}
$$
			- So, we can see that the probability of Y doesn't depend on X at all
- **Probability densities - basics**
	- *Note: there are many, many, formulas in the following sections, I will only write the most important ones*
	- Two key aspects for a probability density $p(x)$
		- $$
\begin{gather}
p(x) \geq 0 \\
\int_{-\infty}^{\infty}p(x) \, dx = 1
\end{gather}
$$
	- Sum + product rules, and Bayes' theorem all apply to probability densities
		- If x and y are two real variables, then
		- $$
\begin{gather}
\text{sum rule} \qquad p(x) = \int p(x, y) \, dy \\
\text{product rule} \qquad p(x, y) = p(y|x)p(x) \\
\text{Bayes' theorem} \qquad \frac{p(x|y)p(y)}{p(x)} \\
\text{p(x) given by} \qquad \int p(x|y)p(y)dy
\end{gather}
$$
- **Expectations and covariances**
	- Expectation of $f(x)$ --> the weighted average of some function $f(x)$ under a probability distribution $p(x)$
		- Denoted by $\mathbb{E}[f]$
		- $$
\begin{gather}
\text{Discrete case} \quad \mathbb{E}[f] = \sum_{x}p(x)f(x) \\
\text{Continous case} \quad \mathbb{E}[f] = \int p(x)f(x) \, dx
\end{gather}
$$
		- If we are given a finite number N points drawn from the probability distribution, then the expectation can be approximated as a finite sum over those points (so just taking the mean)
			- That approximation becomes exact expectation as N goes to infinity
	- *Variance of $f(x)$* provides a measure of how much $f(x)$ varies around its mean value, $\mathbb[E][f(x)]$
		- $$
var[x] = \mathbb{E}[x^2] - \mathbb{E}[x]^2
$$
		- The specific definition above is the variance of the variable x itself, and seems to be the most commonly used in the course
	- *Covariance between x and y*
		- Measures the extent to which the two variables vary together:
		- $$
\begin{align*}
cov[x, y] \quad &= \mathbb{E}_{x,y}[\{x-\mathbb{E}[x]\}\{y-\mathbb{E}[y]\}] \\
&= \mathbb{E}_{xy}[xy]-\mathbb{E}[x]\mathbb{E}[y]
\end{align*}
$$
		- If x and y are independent then their covariance equals zero
- **Gaussian distribution**
	- *The normal or Gaussian distribution*
		- For a single real-valued variable $x$ it is defined as:
		- $$
N(x|\mu,\sigma^2) = \frac{1}{(2\pi \sigma^2)^{1/2}}\text{exp}\left[ -\frac{(x-\mu)^2}{2\sigma^2} \right]
$$
		- ![[Pasted image 20261016163005.png]]
		- Three key terms:
			- $\mu$ is called the *mean*
			- $\sigma^2$ is called the *variance*, while $\sigma$ is called the *standard* *deviation*
			- $\beta=1/\sigma^2$ is called the *precision*
		- Gaussian distribution satisfies:
			- $$
\begin{gather}
\mathcal{N}(x|\mu,\sigma^2) > 0 \\
\int_{-\infty}^{\infty} \mathcal{N}(x|\mu,\sigma^2) \, dx = 1 
\end{gather}
$$
			- Thus, the Gaussian satisfies the two requirements for a valid probability distribution
- **Mean and variance of a Gaussian**
	- The average value of x is given by:
		- $$
\mathbb{E}[x] = \int_{-\infty}^{\infty}\mathcal{N}(x|\mu,\sigma^2) \, x \, dx = \mu 
$$
		- The integral above is also known as the *first order moment*
	- Second order moment is just:
		- $$
\mathbb{E}[x^2] = \int_{-\infty}^{\infty}\mathcal{N}(x|\mu,\sigma^2) \, x^2 \, dx = \mu^2+\sigma^2 
$$
	- *Variance* of $x$ is given by:
		- $$
var[x] = \mathbb{E}[x^2] - \mathbb{E}[x]^2 = \sigma^2
$$
- **Likelihood function**
	- *Density estimation*
		- $X = (x_{1}, \dots, x_{N})$, representing N observations of a scalar variable $x$
		- We will suppose that the observations are drawn independently from a Gaussian distribution, but the mean $\mu$ and variance $\sigma^2$ are unknown
		- Our job --> determine what they are from the dataset
			- Known as density estimation
	- Ill-defined vs. well-defined
		- Ill-defined if we have the space as *all* distributions, but well defined if we constraint the space to be Gaussians
	- *Independent and identically distributed* --> data points that are drawn independently from the same distribution
		- Joint probability of independent events is: $p(X, Y) = p(X)p(Y)$
		- So, we can write the probability of the data set, given a particular $\mu$ and $\sigma^2$
		- $$
p(\mathbf{x}|\mu,\sigma^2)=\prod^N_{n=1}\mathcal{N}(x_{n}|\mu,\sigma^2)
$$
		- ![[Pasted image 20261016173520.png]]
			- *Note: the red curve is not necessarily the optimal Gaussian*
	- *Maximum likelihood idea*
		1. Fix the data (gray dots shown above)
		2. Pick a $\mu$ and $\sigma^2$, which creates a Gaussian curve (red)
		3. Read off the curve's height above each gray data point (blue dots)
		4. Multiply them together, this gets you the likelihood of that particular $\mu$ and $\sigma^2$
		5. Best parameters --> those that maximize the likelihood function
	- *Log likelihood function*
		- More convenient to maximize the log likelihood function
		- Two reasons:
			1. Simplifies the subsequent mathematical analysis
			2. Helps numerically because the product of a large number of small probabilities can easily underflow the precision of the computer
		- $$
\ln p(\mathbf{x}|\mu,\sigma^2)=-\frac{1}{2\sigma^2} \sum^N_{n=1} (x_{n}-\mu)^2-\frac{N}{2}\ln \sigma^2-\frac{N}{2}\ln(2\pi)
$$
	- *Maximizing log likelihood function w.r.t parameters*
		- w.r.t. $\mu$
			- $$
\mu_{ML}=\frac{1}{N}\sum^N_{n=1}x_{n}
$$
		- w.r.t. $\sigma^2$
			- $$
\sigma^2_{ML} = \frac{1}{N}\sum^N_{n=1}(x_{n}-\mu_{ML})^2
$$
		- *Note: the solution for $\mu$ doesn't depend on $\sigma^2$, so we first evaluate $\mu_{ML}$ and then use this result to evaluate $\sigma^2_{ML}$
- **Bias of maximum likelihood**
	- Main conclusion --> maximum likelihood widely used, but has limitations
	- *Bias in mean and variance*
		- $$
\begin{align*}
\mathbb{E}[\mu_{ML}] \quad &= \quad \mu \\
\mathbb{E}[\sigma^2_{ML}] \quad &= \quad (\frac{N-1}{N})\sigma^2
\end{align*}
$$
		 - Conclusions:
			 - ML mean --> will equal the true mean when averaged over data sets of a given size
			 - ML variance --> underestimates the true variance by a certain factor
		 - Why does bias arise in the variance? --> because it the variance is calculated using the sample mean, not the true mean
	 - *Tying into rest of course and conclusions*
		 - But what does it mean for the ML mean to equal the true mean?
			1. Fix a dataset size N, say N = 3.
			2. Draw a dataset of 3 points from the true Gaussian and compute μ_ML.
			3. Throw it away, draw a fresh 3 points, and compute μ_ML again.
			4. Repeat forever, then average all those μ_ML values.
			5. So, it holds for *any* value of N, doesn't matter how small or big your datasets are
		- This is not the case for variance
			- The points will be centered around the correct mean (averaged), but the spread will be wrong
			- And it will be very wrong for small values of N
- **Linear regression**
	- *Linear --> Gaussian*
		- Express our uncertainty over the value of the target variable ($y$) using a probability distribution
		- We will assume that, given the value of $t$, the corresponding value of $y$ has a Gaussian distribution with a mean equal to the value of $\hat{y}(t, \mathbf{w})$ [^1]
			- $$
p(y|t, \mathbf{w}, \sigma^2 ) = \mathcal{N}(y|\hat{y}(t, \mathbf{w}), \sigma^2)
$$
	- *Likelihood function revisited*
		- Use the training data $\{\mathbf{t},\mathbf{y}\}$ to determine the values of the unknown Gaussian parameters $\mathbf{w}$ and $\sigma^2$ by maximum likelihood
		- Assume i.i.d:
			- $$
p(\mathbf{y}|\mathbf{t}, w, \sigma^2)=\prod^N_{n=1}\mathcal{N}(y_{n}|\hat{y}(t_{n};\mathbf{w}),\sigma^2)
$$
		- We can again maximize the logarithm of the likelihood function instead:
			- $$
\ln p(\mathbf{y}|\mathbf{t},w,\sigma^2)=-\frac{1}{2\sigma^2}\sum^N_{n_{1}}\{\hat{y}(t_{n};\mathbf{w})-y_{n}\}^2-\frac{N}{2}\ln \sigma^2-\frac{N}{2}\ln(2\pi)
$$
		- Vital facts for determining the coefficients $\mathbf{w}$
			- The last two terms can be omitted because they don't depend on $\mathbf{w}$
			- Scaling the log likelihood by a positive constant coefficient does not alter the location of the maximum w.r.t. $\mathbf{w}$
				- So --> replace $1/2\sigma^2$ with $1/2$
	- *Connection with linear least squares*
		- Minimizing the negative log likelihood is equivalent to maximizing the log likelihood
		- So, maximizing the likelihood is equivalent to minimizing the *sum-of-squares error function* defined by:
		- $$
E(\mathbf{w}) = \frac{1}{2}\sum^N_{n=1}\{\hat{y}(t_{n};\mathbf{w})-y_{n}\}^2
$$
	- *Determining $\sigma^2$ and wrap-up*
		- $$
o^2_{ML} = \frac{1}{N}\sum^N_{n=1}\{\hat{y}(t_{n};\mathbf{w}_{ML})-y_{n}\}^2
$$
		- Similar to regular maximum likelihood, we first determine the parameter vector $\mathbf{w}_{ML}$ governing the mean, and then use that value to find the variance
		- With the parameters w and $\sigma^2$ we can now make predictions for new values of $t$

## Chapter 3

#### 3.2 - The Multivariate Gaussian 
- *Gaussian Intro*
	- One dimensional Gaussian has $\mu$ mean and $\sigma^2$ variance:
		- $$
\mathcal{N}(x|\mu,\sigma^2) = \frac{1}{(2\pi \sigma^2)^{1/2}}\exp\left\{ -\frac{1}{2\sigma^2}(x-\mu)^2 \right\}
$$
	- For a D-dimensional vector $\mathbf{x}$ the multivariate Gaussian distribution takes the form
		- $$
\mathcal{N}(\mathbf{x}|\mathbf{\mu}, \mathbf{\Sigma}) = \frac{1}{(2\pi)^{D/2}} \frac{1}{|\mathbf{\Sigma}|^{1/2}}\exp\left\{ -\frac{1}{2}(\mathbf{x}-\mathbf{\mu})^T \mathbf{\Sigma^{-1}}(\mathbf{x}-\mathbf{\mu}) \right\}
$$
		- In this case, $\mathbf{\mu}$ is the D-dimensional mean vector, while $\mathbf{\Sigma}$ is the $D \times D$ covariance matrix, and det $\mathbf{\Sigma}$ denotes the determinant of $\mathbf{\Sigma}$
- *Gaussian applications*
	- Consider the sum of multiple random variables
	- *Central limit theorem* tells us that the sum of random variables looks more and more like a Gaussian as the number of terms increase

#### 3.2.1 Geometry of the Gaussian 
- *Mahalanobis distance*
	- Defined as the distance from $\mathbf{\mu}$ to $\mathbf{x}$ 
	- Important: reduces to the Euclidean distance only when $\mathbf{\Sigma}$ is the identity matrix
	- $$
\Delta^2 = (\mathbf{x} - \mathbf{\mu})^T \mathbf{\Sigma}^{-1}(\mathbf{x} - \mathbf{\mu})
$$
- *Gaussian properties*
	- Necessary for all the eigenvalues $\lambda_{i}$ of the covariance matrix to be strictly positive, otherwise the distribution cannot be properly normalized
	- *Positive definite* --> a matrix whose eigenvalues are strictly positive
	- *Positive semidefinite* --> all the eigenvalues are non-negative

#### 3.2.2 Moments
- *Expectation of $\mathbf{x}$* 
	- $$
\begin{aligned}
\mathbb{E}[\mathbf{x}] &= \frac{1}{(2\pi)^{D/2}} \frac{1}{|\mathbf{\Sigma}|^{1/2}}\, \int \exp\left\{ -\frac{1}{2}(\mathbf{x}-\mathbf{\mu})^T \mathbf{\Sigma^{-1}}(\mathbf{x-\mathbf{\mu}}) \right\}\, \mathbf{x} \,dx \\ 
&= \frac{1}{(2\pi)^{D/2}} \frac{1}{|\mathbf{\Sigma}|^{1/2}}\, \int \exp\left\{ -\frac{1}{2}\mathbf{z}^T \mathbf{\Sigma^{-1}}\mathbf{z} \right\}\, (\mathbf{z} +\mathbf{\mu}) \,dz
\end{aligned}
$$
	- Changed variables using $\mathbf{z} = \mathbf{x} - \mathbf{\mu}$
	- By taking the integral from $(-\infty, \infty)$, we get
	- $$
\mathbb{E}[\mathbf{x}] = \mathbf{\mu}
$$
- *Second order moment of the Gaussian*
	- Group the $D^2$ second-order moments together given by $\mathbb{E}[x_{i}, x_{j}]$
	- This can be grouped together to form the matrix $\mathbb{E}[\mathbf{x}\mathbf{x}^T]$
	- By making using of symmetry, the second order moment can be written as
		- $$
\mathbb{E}[\mathbf{x}\mathbf{x}^T]=\mathbf{\mu}\mathbf{\mu^T} + \mathbf{\Sigma}
$$
	- For the 1-D case, we subtracted off the mean before taking the second moment. Similar case here, which gives us the *covariance* of a random vector $\mathbf{x}$ 
		- $$
\text{cov}[\mathbf{x}] = \mathbb{E}[(\mathbf{x}-\mathbb{E}[\mathbf{x}])(\mathbf{x}-\mathbb{E}[\mathbf{x}])^T]
$$
	- For a Gaussian distribution, make use of $\mathbb{E}[\mathbf{x}] = \mathbf{\mu}$ and result (3.46) from the book to give
		- $$
\text{cov}[\mathbf{x}] = \mathbf{\Sigma}
$$
	- Thus, this is why we call $\mathbf{\Sigma}$ the covariance matrix

#### 3.2.7 Maximum likelihood
- *Problem set-up*
	- Given a data set $\mathbf{X} = (\mathbf{x_{1}, \mathbf{x_{2}, \dots, \mathbf{x_{N}}}})^T$ in which the observations $\{\mathbf{x_{n}}\}$ are assumed to be drawn independently from a multivariate Gaussian distribution...
	- Estimate the parameters of the distribution through maximum likelihood
- *Maximum likelihood*
	- Log likelihood function is given by
		- $$
\ln p(\mathbf{X}|\mathbf{\mu}, \mathbf{\Sigma}) = -\frac{ND}{2}\ln(2\pi)-\frac{N}{2}\ln|\mathbf{\Sigma}|-\frac{1}{2} \sum^N_{n=1}(\mathbf{x_{n}-\mathbf{\mu}})^T \mathbf{\Sigma}^{-1}(\mathbf{x_{n}-\mathbf{\mu}})
$$
	- By rearrangement and distributive property, see that the likelihood function is only connected to the dataset through two quantities
		- $$
\sum^N_{n=1}\mathbf{x_{n}} \qquad \sum^N_{n=1}\mathbf{x_{n}}\mathbf{x_{n}}^T
$$
		- These are known as the *sufficient statistics* for the Gaussian distribution
	- Derivatives for maximum likelihood
		- w.r.t. $\mathbf{\mu}$
			- $$
\begin{aligned}
\frac{\partial}{\partial \mathbf{\mu}} = \ln p(\mathbf{X}|\mathbf{\mu}, \mathbf{\Sigma}) &= \sum^N_{n=1} \mathbf{\Sigma}^{-1}(\mathbf{x_{n}}-\mathbf{\mu}) \\
\mathbf{\mu_{ML}} &= \frac{1}{N}\sum^N_{n=1}\mathbf{x_{n}}
\end{aligned}
$$
		- w.r.t. $\mathbf{\Sigma}$ is more complicated.., but solution is
			- $$
\mathbf{\Sigma_{ML}} = \frac{1}{N}\sum^N_{n=1} (\mathbf{x_{n}-\mathbf{\mu_{ML}}})(\mathbf{x_{n}-\mathbf{\mu_{ML}}})^T
$$
- *Expectation of maximum likelihood and bias*
	- Evaluate the expectation of the maximum likelihood under the true distribution
	- $$
\begin{aligned}
\mathbb{E}[\mathbf{\mu_{ML}}] \quad &= \quad \mathbf{\mu} \\ 
\mathbb{E}[\mathbf{\Sigma_{ML}}] \quad &= \quad \frac{N-1}{N}\mathbf{\Sigma}
\end{aligned}
$$
	- See that the expectation of the maximum likelihood estimate for the mean --> equal to the true mean
	- Maximum likelihood estimate for covariance --> less than the true value, so, it is biased

#### 3.2.9 Mixtures of Gaussians
- *Introduction*
	- Gaussian suffers from limitations when used to model real data sets
	- ![[Pasted image 20261109091457.png|572]]
	- Consider the above case
		- Dataset --> 'Old Faithful' geyser in Yellowstone with 272 measurements 
		- Each measurement gives the duration of the eruption in minutes (horizontal axis) and the time in minutes to the next eruption (vertical axis)
		- Two dominant clumps, and figure (a) is unable to capture this structure
		- Figure (b) is known as a *mixture distribution* and does a much better job at capturing the dataset
- *Formal definitions*
	- Consider a superposition of $K$ Gaussian densities of the form
		- $$
p(\mathbf{x}) = \sum^K_{k=1}\pi_{k}\mathcal{N}(\mathbf{x}|\mathbf{\mu_{k}}, \mathbf{\Sigma_{k}})
$$
		- This is called a *mixture of Gaussians*
	- Each Gaussian density $\mathcal{N}(\mathbf{x}|\mathbf{\mu_{k}}, \mathbf{\Sigma_{k}})$
		- Called a *component* of the mixture
		- Has its own mean $\mu_{k}$ 
		- Has its own covariance $\mathbf{\Sigma_{k}}$
	- Parameters $\pi_{k}$ are called *mixing coefficients*
		- Given that the individual Gaussian components and $p(\mathbf{x})$ are both normalized..
			- $$
\sum^K_{k=1}\pi_{k} = 1
$$
		- Also, given that $\mathcal{N}(\mathbf{x}|\mathbf{\mu_{k}}, \mathbf{\Sigma_{k}}) \geq 0$, combine this with the prior equation to get
			- $$
0 \leq \pi_{k} \leq 1
$$
- *Writing as sum/product rule*
	- $$
p(\mathbf{x}) = \sum^K_{k=1}p(k)p(\mathbf{x}|k)
$$
	- Relating to the original equation, we find that
		- $\pi_{k} = p(k)$, which is the prior probability of picking the kth component
		- $\mathcal{N}(\mathbf{x}|\mathbf{\mu_{k}}, \mathbf{\Sigma_{k}}) = p(\mathbf{x}|k)$, which is the probability of data $\mathbf{x}$ conditioned on component k
	- More details are given on page 88
- *Log likelihood of Gaussian mixture model*
	- Gaussian mixture distribution is governed by the parameters $\mathbf{\pi, \mu, \Sigma}$, where:
		- $$
\begin{gather}
\mathbf{\pi} = \{\pi_{1}, \dots, \pi_{K}\} \\
\mathbf{\mu} = \{\mathbf{\mu_{1}, \mu_{2}, \dots, \mu_{K}}\} \\
\mathbf{\Sigma} = \{\mathbf{\Sigma_{1}, \dots, \mathbf{\Sigma_{K}}}\}
\end{gather}
$$
	- The log likelihood can be given by
		- $$
\ln p(\mathbf{X}|\mathbf{\pi}, \mathbf{\mu, \Sigma}) = \sum^N_{n=1}\ln\left\{ \sum^K_{k=1}\pi_{k}\mathcal{N}(\mathbf{x_{n}} |\mathbf{\mu_{k}, \mathbf{\Sigma_{k}}}) \right\}
$$
		- Note that the maximum likelihood solution for the parameters no longer has a closed-form solution


## Chapter 4 

#### Chapter 4.1.6 Regularized Least Squares
- *Introduction*
	- Idea --> add a regularization term to an error function to control over-fitting
		- $$
E_{D}(\mathbf{w}) + \lambda E_{W}(\mathbf{w})
$$
		- here, $\lambda$ is the regularization coefficient that controls the importance of the $E_{W}$ term 
- *Sum of squares*
	- One of the simplest forms --> sum of the squares of the weight vector elements:
		- $$
E_{W}(\mathbf{w}) - \frac{1}{2}\sum_{j}w^2_{j} = \frac{1}{2}\mathbf{w}^T\mathbf{w}
$$
	- Then we can also apply the classic sum-of-squares error function [^1]:
		- $$
E_{D}(\mathbf{w})=\frac{1}{2}\sum^N_{n=1}\{t_{n}-\mathbf{w}^T \mathbf{\phi}(\mathbf{x_{n}})\}^2
$$
	- Then, the total error function becomes:
		- $$
\frac{1}{2}\sum^N_{n=1}\{t_{n}-\mathbf{w}^T \mathbf{\phi}(\mathbf{x_{n}})\}^2 + \frac{\lambda}{2}\mathbf{w}^T \mathbf{w}
$$
- *Error interpretation*
	- Regularizer --> example of *parameter shrinkage* because the parameter vector $\mathbf{w}$ gets shrunk towards zero
	- The regularized least squares solution still has a closed form solution [^2]
		- Obtained by setting the gradient of the above equation with respect to $\mathbf{w}$ to zero and solving:
		- $$
\mathbf{w} = (\lambda I+\Phi^T \Phi)^{-1}\Phi^T\mathbf{t}
$$

#### Chapter 4.3 Bias-Variance Trade-off
- *Introduction*
	- To avoid overfitting --> limit the number of basis functions (degrees of freedom of the model)
	- This has the side effect of limiting the flexibility of the model to capture interesting and important trends in the data
	- So, how to determine a suitable value for $\lambda$?
	- Consider a frequentist viewpoint of the mode complexity --> known as the *bias-variance* trade-off
- *Loss function definition*
	- Expected squared loss can be written in the form:
		- $$
\mathbb{E}[L] = \int\{f(\mathbf{x}-h(\mathbf{x}))\}^2 p(\mathbf{x})\,d\mathbf{x} + \int \int\{h(\mathbf{x})-t\}^2p(\mathbf{x}, t)\,d\mathbf{x}\,dt
$$
	- The second term is independent of our chosen function $f(\mathbf{x})$
		- It arises from the intrinsic noise on the data
		- So, it is the minimum achievable value of the expected loss
	- The first term actually does depend on our function choice
		- So --> seek a solution for $f(\mathbf{x})$ that makes this first term a minimum
	- What are we limited by?
		- In practice, we are limited by a dataset $D$ containing only a finite number $N$ data points
		- So, we can't know the true regression function $h(\mathbf{x})$ exactly
- *Bias and variance*
	- Idea --> find an average performance
		- Assume a large number of data sets, each of size $N$, where each is drawn independently from the distribution $p(t, \mathbf{x})$
		- For any given data set $D$ we can run our learning algorithm and obtain a predictive function for that dataset: $f(\mathbf{x};D)$
		- Different data sets will result in different functions and different values for the loss
		- Performance of a particular learning algorithm --> assessed by taking the average over this ensemble of data sets
	- To find the expectation of the expression with respect to $D$, we get: (*note, more details on page 125*)
		- $$
\begin{aligned}
\mathbb{E}_{D} &[\{f(\mathbf{x};D)-h(\mathbf{x})\}^2] \\
= \, &\{\mathbb{E}_{D}[f(\mathbf{x}; D)] -h(\mathbf{x})\}^2 + \mathbb{E}_{D}[\{f(\mathbf{x};D)-\mathbb{E}_{D}[f(\mathbf{x};D)]\}^2]
\end{aligned}
$$
		- The term to the left of the $+$ is the $\text{bias}^2$, while the term to the right is simply the variance
	- Definitions:
		- Squared *bias* --> represents the extent to which the average prediction over all data sets differs from the desired regression function
		- *Variance* --> measures the extent to which the solutions for individual data sets vary around their average
	- Loss formula:
		- $$
\text{expected loss} = (\text{bias})^2 + \text{variance} + \text{noise}
$$
		- Full formulas on page 125
- *Problem example*
	- Set-up:
		- Goal is to minimize the expected loss
		- 100 independently generated data sets, each one containing $N = 25$ data points from the underlying regression curve $h(x) = \sin(2\pi x)$
		- Data sets are indexed by $l = 1, \dots, L$, where L = 100
		- For each dataset, a model is fit with $M = 24$ Gaussian basis functions along with a constant bias function, $\lambda$ to give 25 parameters
	- Trade-off between bias and variance:
		- Very flexible models --> low bias and high variance
		- Rigid models --> high bias and low variance
		- Optimal model --> the one that leads to the best balance between bias and variance
	- ![[Pasted image 20261110120310.png|569]]
		- Top row:
			- Large value of the regularization coefficient $\lambda$ that vies low variance (because the red curves in the left plot look similar)
			- But high bias (because the red average and the green curve are very different)
			- This is because the weights are heavily penalized, resulting in a simpler model
		- Bottom row:
			- Small value of the regularization coefficient 
			- Large variance --> high variability between the red curves in the left plot
			- Low bias --> shown by the good fit between the average model fit and the original sinusoidal function 
		- This generally suggests that averaging may be a beneficial procedure because of how good the fit is
- *Formal definitions*
	- The average prediction is estimated from:
		- $$
\bar{f}(x) = \frac{1}{L}\sum^L_{l=1}f^{(l)}(x)
$$
	- The integrated squared bias and integrated variance are then given by:
		- $$
\begin{aligned}
(\text{bias})^2 &= \frac{1}{N}\sum^N_{n=1}\{\bar{f}(x_{n})-h(x_{n})\}^2 \\
\text{variance} &= \frac{1}{N}\sum^N_{n=1} \frac{1}{L}\sum^L_{l=1}\{f^{(l)}(x_{n})-\bar{f}(x_{n})\}^2
\end{aligned}
$$



[^1]: Note: the textbook uses x for the input and t for the target. In class, we use t for the input and y for the target.

[^2]: Notation: textbook uses $\Phi$ for $A$ and $\mathbf{t}$ for $\vec{y}$
