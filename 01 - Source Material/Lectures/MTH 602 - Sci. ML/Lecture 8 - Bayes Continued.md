2026-10-05 11:10

Course: #mth602 

## Big Ideas

*quick summary of ideas - 3-5 bullet points max*
- L2-norm is a bad idea of comparing distributions because the L2 norm can be similar, but the actual distribution shape be very different
- KL-Divergence is a way of comparing distributions by quantifying the information lost in bits/nats
- Refer to casino example with dice, casino could lose $10k per hand if they set up their payout wrong
- Short intro on entropy: Boltzmann and Shannon entropy

## Key Concepts

*place links to full notes here*

## Notes
- How to compare closeness of two probability distributions of $P(x), Q(x)$
	- Example of what not to do - use L2 norm
		- $x \in \{x_{i}, x_{2}, x_{3}\}$
		- Ground truth (target distribution): $p=(.8, .2, 0)$
		- Two possible distributions:
			- $Q_{1}=(.6, .4, 0)$
			- $Q_{2}=(.8,0,.2)$ --> this one is particularly bad because x3 should *never* occur
		- Want to know which is closer to ground truth: $Q_{1} \text{ or } Q_{2}$
		- Simple idea: these are vectors, so take L2 norm, right?
		- $$
\begin{gather}
||\vec{P}-\vec{Q_{1}} ||_{2}^2 \\
= \sum_{i=1}^3(P_{i}-Q_{i}^1)^2
\end{gather}
$$
		- Illustrated example in slides: three distributions with the same L2 norm, but their actual probability density function looks very different
- Fair coin game example
	- Setup:
		- $$
\begin{gather}
P(X=H) = 0.9 & P(X=T)=0.1 \\ \\
\text{Payout(x)}=
\begin{cases}
\frac{1}{.9} & x=H \\
\frac{1}{.1} & x=T
\end{cases} \\
\text{WinningA(x)} = 
\begin{cases}
\frac{1}{.9} & x=H \\
0 & x=T
\end{cases}
\end{gather}
$$
	- Compute expectation value for player A (should be 1 for fairness)
		- $E[WA(x)]=(.9)\left( \frac{1}{.9} \right)+(.1)(0) = 1$
	- Mistake "1"
		- Casino thinks the coin isn't fair anymore
		- So, they change their payout for the expectation to be 1 again
		- $$
\begin{gather}
q_{1}(x=H) = 0.8, q_{2}(x=T) = 0.2 \\
Payout(x)=
\begin{cases}
\frac{1}{.8} & x=H \\
\frac{1}{.2} & x=T
\end{cases} \\
\text{So, then, we compute the expected payout for WA(x)} \\
\begin{cases}
\frac{1}{.8} & x=H \\
0 & x=T
\end{cases} \\
\text{Now, we compute "true" expectation} \\
E[WA(x)]=(.9)\left( \frac{1}{.8} \right)+0=1.125 \text{ so they are winning now!}
\end{gather}
$$
	- There is another extreme example: where the casino thinks the chance of heads is like .999999 and tails is $10^{-6}$
		- This results in an extremely large payout for tails, despite the "true" tails chance being 10%
		- So, Player B, who always bets on tails, ends up winning 100,000 dollars per hands
- Kullback-Letter Divergence - the "better" way
	- $$
KL(P||Q) = \int P(x)\left[ \log_{b} \frac{P(x)}{Q(x)} \right]dx = -\int P(x)\left[ \log_{b} \frac{Q(x)}{P(x)} \right]dx
$$
	- *where P is the true and Q is the approx. and b can be 2 or e (standard)*
	- b=2 --> bits, b=e --> nats
- Example using KL-Divergence
	- Using the distribution where H=0.8 instead of 0.9
	- $$
KL(P||Q_{1})=-\sum_{x\in\{H,T\}}P(x)\log_{2} \frac{Q_{1}(x)}{P(x)}\approx.053\text{ bits}
$$
	- The super bad one, where H=0.999999 results in 1.52 bits
	- Assigning a probability of zero to a true probability results in infinite KL-Divergence
		- (think of the casino example, imagine a tails shows up when the casino thinks its literally impossible)
- Two facts of KL-Divergence
	1) KL(P||Q) >= 0
	2) KL(P||Q) = 0 if and only if P=Q
- Another example
	- X is a random variable
	- N observations: $\vec{x}=(x_{1}, x_{2}, \dots, x_{N})$
	- Assume $x \sim \mathcal N(x|\mu,\sigma^2)$ and x's are i.i.d.
		- The true is $P(X)$ and the parameterized $\mathcal N: \mathcal N(x|\mu,\sigma^2)$
	- Minimized Kl solution = $\mu_{KL},\sigma^2_{KL}=min_{\mu,\sigma^2}KL(P||\mathcal N(x|\mu,\sigma^2))$
- Entropy intro
	- Boltzman entropy = $K_{B}(\ln w)$
		- *where Kb is Boltzmann's constant and w is the number of microstates consistent with the macrostate*
	- Shannon Entropy
		- $H[P]=-\int P(x) \log_{b}P(x)$
		- If b=e, then: $=-\int P(x)\ln P(x)$



## Questions/Gaps/Concerns



## Follow-up 

*actions items to follow-up on (e.g., watch video, re-read notes, hw)*



## References

*link to other notes, attachments, or actual lecture slides*
