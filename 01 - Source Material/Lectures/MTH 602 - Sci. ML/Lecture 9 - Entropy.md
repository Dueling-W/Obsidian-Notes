2026-10-07 11:21

Course: #mth602 

## Big Ideas

*quick summary of ideas - 3-5 bullet points max*

## Key Concepts

*place links to full notes here*

## Notes
- Question: how many microstates can you arrange N flips with a fair coin?
	- It is just $2^N$, call this W, possible sequences you can observe
	- Probability of observing any particular sequence: 
	- $$
P = \frac{1}{W} = 2^{-N}
$$
	- $$
\begin{gather}
H[P] = -\sum_{\text{all microstates}}P(X_{i})[\log_{2}P(X_{i})] \\
=-(2^N)(2^{-N})(-N) = N \\
\text{High entropy because everything is equally likely}
\end{gather}
$$
- Intuition with Boltzman's entropy
	- More ways that you can arrange particles to the right --> higher total value
		- Combinations
	- For example $\Omega$ = 10 when you can move one particle because you could move any of the 10 particles
- Particle problem using Shannon entropy
	- $H = -\sum P_{i}\ln P_{i}$
	- For Boltzman, usually sum over a fixed macrostate (such as when you can move 2 particles at a time to the right), $\Omega = 45$
	- $P_{i} = \text{ constant for ith microstate}$
	- W = all microstates, which is $P_{i}=\frac{1}{W}$
	- $$
\begin{gather}
H = - \sum P_{i}(\ln P_{i})=-\sum \frac{1}{w}\left( \ln \frac{1}{w} \right)=\sum \frac{1}{w}\ln w=(w)\left( \frac{1}{w} \right)(\ln W) = \ln W
\end{gather}
$$
- Big comparison between Shannon and Boltzman

| Shannon                   | Boltzman                                           |
| ------------------------- | -------------------------------------------------- |
| Outcomes                  | Microstates                                        |
| 1 coin flipped<br>2 times | 2 particles each of which <br>can be left or right |
| {HH, HT, TH, TT}          | {LL, LR, Rl, RR}                                   |
- Talking more about Shannon entropy and self-information
	- $$
\begin{gather}
H[P] = -\sum_{i \in \text{ outcomes}}P(X_{i})[\log_{2}P(X_{i})] =  \\ \\
E_{x \sim P}[-\log_{b}P(X)]=-\log_{2}P(X=X_{i}) =  \\
\text{Self-information of  } X=X_{i} \\
I(X=X_{i}) = -\log_{2}P(x_{i})
\end{gather}
$$
	- Intutition behind the self-information and facts:
		- Goes to 0 as the probability goes to 1
		- Becomes unboundedly large as probability goes to 1
		- If you didn't win in Powerball, you likely wouldn't tell anybody
		- If you won in Powerball, that's a lot of information, so you would tell people
	- $$
\log[P(X_{1})P(X_{2})] = \log P(X_{1})+\log P(X_{2})
$$
- Another example about self-information gain
	- N flips = 4
	- $P(H)=P(T)=\frac{1}{2}$
	- $2^4=16$ possible combinations
	- If you are trying to guess the sequence and you say "Is it TTHH?" and the answer is no, you only changed the distribution from $\frac{1}{16}$ to $\frac{1}{15}$, very little information gained
- Another example
	- $P(X=H)=0.9$ and $P(X=T)=0.1$
	- ![[Pasted image 20261007120721.png]]
	- Person A wants to communicate information to person B
- Check expectation values for the different encodings

## Questions/Gaps/Concerns



## Follow-up 

*actions items to follow-up on (e.g., watch video, re-read notes, hw)*



## References

*link to other notes, attachments, or actual lecture slides*
