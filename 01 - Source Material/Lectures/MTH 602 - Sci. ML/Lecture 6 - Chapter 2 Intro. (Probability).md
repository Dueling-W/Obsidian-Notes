2026-09-23 11:00

Course: #mth602

## Big Ideas

*quick summary of ideas - 3-5 bullet points max*

## Key Concepts

*place links to full notes here*

## Notes
- Joint distribution represented as P(X, Y):
	- Probability of X and Y
- Probability distribution normalization property --> sum of all possibilities must equal 1 and no probabilities can be negative
- What if you don't care about some random variables?
	- Can perform marginal distribution
	- $$
P(X) = \sum_{y \in \text{ outcomes}} P(X, Y = y)
$$
- Conditional distribution
	- $$
P(Y | X) = \frac{P(X, Y)}{P(X)}
$$
	- Probability of Y given X
- Empirical distribution/estimate
	- $$
P(X=x_{i}, Y=y_{j}) = \frac{n_{ij}}{N}
$$
- Easy example --> your y-axis can be Y=1 (not raining) or Y=2 (raining)
	- The x-axis would be 9 bins: each representing a range of cloud cover (such as 0-10% cloud cover)
- Let's compute a few different histograms:
	- $$
\begin{gather} \\
\text{Conditional Probabilities} \\
P(X, Y) = P(X | Y)P(Y) \\
P(X, Y=1) = P(X|Y=1)P(Y=1)
\end{gather}
$$
	- Now what does each of these really mean?
	- $$
\begin{gather}
\frac{n_{i1}}{N} \to P(X=X_{i}, Y = 1), \text{ look up a given x in its bin, sum if Y = 1} \\
P(Y=1) \to \sum_{i=1}^{9} \frac{n_{i1}}{N}
\end{gather}
$$
- Transition to continuous probability distributions
- Definitions:
	- x --> is a continuous random variable
	- P(X) is called the probability density function
	- $$
\begin{gather}
0 \leq P(X) \to \text{the actual value can be very large, but non-negative} \\
\int P(X)dx = 1 \\
\text{Probability of observing } x \in \left[ x_{0}-\frac{x}{2} \right]
\end{gather}
$$
- Let f(x) be a function of a random variable x
	- The expected value of f(x) is:
	- $$
E_{x \text{ drawn from }P(x)}[f(x)] = \int P(x)f(x)dx = \sum_{x \in \text{ outcomes}}f(x_{i})P(x_{i})
$$
	- The equals sign represents the discrete case
- Example of continuous probability distribution
	- $$
\begin{gather}
x \in [2, 4] \\
P(x) = \frac{1}{4-2} = \frac{1}{2} \\
E[x] = \int_{2}^4P(x)xdx \\
= \int_{2}^4 \frac{x}{2}dx = 3
\end{gather}
$$
	- In this example, we computed the expected value of x, and it came out to be three 
	- This makes sense since the domain is 2, 3, 4. and they are all equally likely
- Variance and more
	- Variance --> how does f(x) "typically" fluctuate
	- $$
\begin{gather}
\text{Let } f(x) \text{ be a function of a random variable } x \\
Var(f(x)) = E[(f(x)-E[f(x)])^2]
\end{gather}
$$
	- Standard deviation --> sqrt of variance
		- More interpret-able because it has the correct units, while variance has units squared (like Celsius squared)
- Example with variance:
	- Playing a game where x can either be Head or Tails
	- $$
f(x) = \begin{cases}
2 & \text{x= Heads} \\
-1 & \text{x= Tails}
\end{cases}
$$
	- $$
E[f(x)]=(P(x=H))(f(H))+(P(x=T))(f(T)) = \left( \frac{1}{2} \right)(2)+\left( \frac{1}{2} \right)(-1) = 1-.5 = .5
$$
	- This means that as you play the game to infinity (N goes to infinity), you will profit .5
	- $$
var(f) = P(x=H)(1.5)^2+P(x=T)(1.5)^2=(1.5)^2, std(f) = 1.5
$$
	- So, a typical play would be: .5 +- 1.5
- Gaussian distribution
	- $N(x|\mu, \sigma^2)$
- Modeling from data: density estimation
	- N observations of a random X: $X_{1}, X_{2}, \dots, X_{n} \to \vec{X}$
	- Example: $y_{i} = s_{i} +n_{i}$, noise at time t_i
- Flips of a coin are an example of i.i.d.
	- independent and identically distributed
	- Identically distributed --> each observation follows the same probability distribution
	- Independent --> each observation is independent from all others
- Investigating a distribution:
	- $$
\begin{gather}
P(\vec{X}) = P(X_{1})P(X_{2}) \dots P(X_{N}) \\
= \prod_{i=1}^NP(X_{i}) \\
= \prod_{i=1}^N N(X=X_{i} | \mu,\sigma^2) \\
= \text{the likelihood function} \\
= L(\mu, \sigma^2;\text{data}) \\
=P(\text{data } | \mu, \sigma^2)
\end{gather}
$$
- Cool plot showing the animation of the log likelihood function (can maybe find on the internet)
- 


## Questions/Gaps/Concerns
- How exactly does E_x work and what are the differences between P(x) and f(x)?


## Follow-up 

*actions items to follow-up on (e.g., watch video, re-read notes, hw)*



## References

*link to other notes, attachments, or actual lecture slides*
