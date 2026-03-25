
## References



## Notes
- Opponent can be unpredictable
	- Specific moves for every possible opponent reply
	- Need approximations --> time limits make it unlikely to find a complete solution
- Game tree
	- Is a two-player deterministic game with alternating turns
- Minimax algorithm
	- Choose a move that positions the player with the highest achievable payoff against the best play from the opponent
	- Properties:
		- Complete: Yes, if the game tree is finite.  
	    - Optimal: Yes, when playing against an optimal opponent.  
	    - Time Complexity: Significant when branching factors and depths are high.  
	    - Space Complexity: Requires depth-first exploration.
- $\alpha-\beta$ Pruning (alpha-beta)
	- Optimizes minimax --> Prune branches that cannot influence the final decision
	- Final result not affected 
	- Effectivness increases with better move ordering
	- Properties
		- If perfect move ordering --> search depth basically doubles
- Resources limits
	- Time/computational capcity limit search depth
	- Standard approaches --> cutoff test (depth limit) and use evaluation functions to estimate desirability
- Evaluation functions
	- Common in chess: weighted sums of features like material advantage or positional strength
	- Proxies for utility functions when full computation is infeasible 
- Cutoff Search
	- Similar to minimax
	- Replace terminal checks with cutoff tests and utility calculations with evaluation function
	- So basically more efficient solution
- Deterministic Games:
	- Checkers: Chinook used precomputed endgame databases to achieve perfect play in specific scenarios.  
    - Chess: Deep Blue defeated Garry Kasparov, leveraging advanced search techniques and evaluation functions.  
    - Go: Early AI struggled due to high branching factors, but AlphaGo's success demonstrated the power of modern approaches

### Minimax Example
- Steps:
	1) Generate whole game tree from root to leaves
	2) Apply utility (payoff) function to all leaves (may be given)
	3) Use DFS for expanding the tree
		1) Goes as deep as possible
	4) Back-up values from leaves towards the root:
		1) A max node computes the maximum value from its children
		2) A min node computes the minimum value from its children
	5) When value reaches the root: optimal move is determined
- Eventually, a particular value will be given to the root node
	- You can find a trace such that each node matches the value on the root node, say 10

### $\alpha - \beta$ Pruning (Alpha Beta)
- A few basic rules
	- $\alpha \geq \beta$ is the pruning condition
	- $\text{MAX} \to \alpha$
	- $\text{MIN} \to \beta$
- Same thing as the minimax example
	- We have a tree with alternating MAX/MIN layers
	- DFS is used for traversal 
- Overall Steps
	 1) Initialize $\alpha$ to $-\infty$ and Initialize $\beta$ to $\infty$
	 2) If node is MIN, only update $\beta$
		 1) Update with smallest value from the children AND prior $\alpha$ and $\beta$ values
	 3) If node is MAX, only update $\alpha$
		 1) Update with the largest value from the children and prior $\alpha$ and $\beta$ values
	 4) If at any point, the pruning condition ($\alpha \geq \beta$) is met, then you prune the tree and you don't have to traverse down that direction
	 5) Continue this process, and eventually propagate the final alpha and beta values back to the root node


