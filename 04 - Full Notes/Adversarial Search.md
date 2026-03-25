
2026-03-11 13:19

Tags: [[artificial intelligence]] [[data structures + algorithms]]

# Adversarial Search


### Brief Introduction to Adversarial Search
- Standard search problems, such as informed search, an agent plans a sequence of actions to reach a goal state.
- Adversarial search arises when another agent (an opponent) is actively working against your goals.
- Core challenge --> opponents behavior is inherently unpredictable.
	- This is because they are making their own strategic decisions.
	- A plan must account for every possible reply they might make.
- A perfect solution is too computationally expensive.
	- Space of possible exchanges grows exponentially with depth - so approximations are necessary.
- Time constraints --> must cut off search early and estimate the quality of positions.
	- Standard approaches --> cutoff test (depth limit) and evaluation functions to estimate desirability.
	- E.g., weighted sums of material advantage or position strength in chess.
	- Proxies can even be used for utility functions when full computation is infeasible.
- Game tree --> a model for adversarial search. 
	- Represents the alternating decisions of both players.
	- Each node --> game state.
	- Each edge --> a legal move.
	- Focus initially on two-player, deterministic, zero-sum games with alternating turns. 
		- Typical example being chess, since one player's gain is exactly the other's loss.
- Cutoff Search --> similar to minimax but more efficient.
	- Replace terminal checks --> cutoff tests.
	- Utility calculations --> evaluation function.
	- All in the name of efficiency.
	- E.g., alpha beta pruning.
- Example of deterministic games:
	- Checkers: Chinook used precomputed endgame databases to achieve perfect play in specific scenarios.  
    - Chess: Deep Blue defeated Garry Kasparov, leveraging advanced search techniques and evaluation functions.  
    - Go: Early AI struggled due to high branching factors, but AlphaGo's success demonstrated the power of modern approaches


### Minimax Algorithm
- Choose a move that positions the player with the highest achievable payoff against the best play from the opponent.
	- Properties:
		- Complete: Yes, if the game tree is finite.  
	    - Optimal: Yes, when playing against an optimal opponent.  
	    - Time Complexity: Significant when branching factors and depths are high. $O(b^m)$
	    - Space Complexity: Requires depth-first exploration. $O(bm)$
- General Steps:
	1) Generate whole game tree from root to leaves
	2) Apply utility (payoff) function to all leaves (may be given)
	3) Use DFS for expanding the tree
		1) Goes as deep as possible
	4) Back-up values from leaves towards the root:
		1) A max node computes the maximum value from its children
		2) A min node computes the minimum value from its children
	5) When value reaches the root: optimal move is determined


- ![[minimax_better_screenshot.png|646]]
	- This screenshot details the overall minimax tree.
	- Each layer is labeled either MAX or MIN.
	- DFS has been used to go all the way down to node 10 (left-hand side).
	- The algorithm back-tracks and stores 10 at the MAX node, then DFS traverses to node 9.
		- But since $10 > 9$ 10 is stored in the MAX node and sent further up to the MIN node. 
	- The algorithm then computes the next MAX node, comparing 14 to 18.
		- Since 18 > 14, 18 is stored in the MAX node.
	- Since 10 < 18, 10 gets to say in the MIN node and is sent back towards the root (a MAX node).
	- The right side of the tree repeats in a similar manner.
	- Eventually, the final result is computed to be 10.

### Alpha-Beta pruning
- An optimization to the minimax algorithm.
	- Idea --> prune branches that cannot influence final result.
	- So, same result as minimax, just faster.
- Effectiveness increases with better move ordering.
	- Best case performance --> happens with perfect move ordering.
	- Changes performance to: $O(b^{m/2})$, effectively doubles search depth vs. plan minimax.

- General Intro:
	- $\alpha \geq \beta$ is the pruning condition.
		- If this becomes true for any node, prune the branch.
	- $MAX \to \alpha$
	- $MIN \to \beta$
- Reference video: [Alpha Beta Example](https://www.youtube.com/watch?v=_i-lZcbWkps&t=3s)
- ![[alpha_beta_screenshot.png]]
	- Now each node has an alpha and beta
		- Initialize $\alpha$ to $-\infty$ and Initialize $\beta$ to $\infty$
	- Bottom node is a MIN node, so we only update $\beta$
		- Since 5 is less than 10 and infinity, it is updated to 5.
	- Next is a MAX node, so we only update $\alpha$
		- Look at current alpha AND alpha/beta of prior node
		- Candidates: $-\infty$, 5, and $-\infty$
			- Of course, 5 is the largest
- This general process continues throughout, making sure to check for pruning, example is shown below:
	- ![[prune_example.png]]
		- Pretty simple, since $\alpha = 7$ and $\beta = 7$ the condition $\alpha \geq \beta$ is satisfied, so the entire branch underneath is pruned.


# References
