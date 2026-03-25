
2026-03-11 08:14

Tags: [[artificial intelligence]] [[data structures + algorithms]]

# Uninformed Search Algorithms

### Uninformed Search Introduction
- Generally described as "blind search" algorithms. 
	- No information about problem state beyond the problem definition.
- Generally described by a scenario, goal, states, actions, and a solution.
	- Example: Romania city problem
	- Scenario: On holiday in Romania; currently in Arad. Flight leaves tomorrow from Bucharest.
	- Goal: Be in Bucharest.
	- States: Various cities.
	- Actions: Driving between cities.
	- Solution: Sequence of cities, e.g., Arad → Sibiu → Fagaras → Bucharest.
- General process for uninformed search algorithms:
	- Generate possible successors --> distinguish a goal state from the rest of the states.
	- Key idea: search strategies only differ by the order in which the nodes (successors) are expanded.
- States vs. Nodes
	- A state is physical configuration of the problem. 
		- E.g., in 8-puzzle problem, a state is simply the current arrangement of tiles on the board. 
	- Nodes, by contrast, are booking structures that exist solely within the search algorithm.
		- A node typically stores the state (configuration), parent node, action, path cost, and depth. 
- Expand function bridges states and nodes.
	- Looks up the applicable actions for that node's state
	- Applies each action to generate a _successor state_
	- Wraps each successor state in a _new node_, filling in the parent pointer (the current node), the action taken, updated path cost, and incremented depth
	- Basically describes how we take an existing node's state and turn it into new successors.

### Uninformed Search Strategies - Brief Intro.
- Evaluation Strategies:
	- Completeness: Does it always find a solution if one exists?  
    - Time Complexity: Number of nodes generated.  
    - Space Complexity: Maximum number of nodes in memory.  
    - Optimality: Does it always find a least-cost solution?
    - Complete: Will the algorithm always find a solution if one exists?
- Space/time complexity defined by:
	- $b$ --> branching factor
	- $d$ --> depth 
	- $m$ --> max depth
	- $l$ --> max depth cutoff for DLS
	- Example of BFS time/space complexity
		- Root generates $b$ nodes at the first level. 
			- Each of these generates $b$ more nodes.
		- Ends up like: $b + b^2 + b^3 + \dots + b^d = O(b^d)$

| Algorithm  | Complete? | Optimal? | Time Complexity | Space Complexity |
| ---------- | --------- | -------- | --------------- | ---------------- |
| BFS        | Yes       | Yes*     | $O(b^d)$        | $O(b^d)$         |
| DFS        | No        | No       | $O(b^m)$        | $O(bm)$          |
| UCS        | Yes       | Yes      | $O(b^{1+C*/e})$ | $O(b^{1+C*/e})$  |
| DLS        | No        | No       | $O(b^l)$        | $O(bl)$          |
| IDS        | Yes       | Yes*     | $O(b^d)$        | $O(bd)$          |

### Uninformed Search Strategies
- Breadth-First Search (BFS)
	- All nodes are expanded at a given depth in the search tree before any nodes at the next level are expanded.
		- Depth = 0, then depth = 1, depth = 2, etc.
	- Data stack is a FIFO queue for the frontier. 
	- Time complexity is scary, along with the memory requirements. 
	- When all step costs are equal --> BFS is optimal.

- Uniform-Cost Search
	- Don't expand shallowest node, instead, expand the node n with the lowest path cost $g(n)$.
	- Store the frontier as a priority queue ordered by $g$. 
	- Don't consider steps, only total cost. 

- Depth-First Search
	- Expand the deepest node in the current frontier.
	- Data stack is a LIFO queue, a stack.
	- Proceeds immediately to the deepest level of the search tree, where the nodes have no successors. 
	- Memory advantage over BFS because DFS only needs to store a single path from the root to a leaf node.
		- Along with the remaining unexpanded sibling nodes.
		- So, it is much less than the entire tree.

- Depth-Limited Search
	- Just DFS with a depth limit, where nodes at the limit have no successors.

- Iterative Deepending Search (IDS)
	- Combines the benefits of BFS and DFS.
	- Uses only linear space with minimal overhead compared to BFS.

