
2026-03-11 09:15

Tags: [[artificial intelligence]] [[data structures + algorithms]]

# Informed Search Algorithms

### General Introduction
- Review: fundamental search strategy is defined by picking the order of node expansion.
- Informed search strategies use heuristic functions.
	- Heuristic functions --> impart additional knowledge of the problem on the search algorithm. 
- This evaluation function is construed as a cost estimate.
	- Identical to uniform-cost search.
	- Except, function $f$ is used in-place of $g$ to order the priority queue.
	- The chosen definition of $f$ is the search strategy.
- Most best-first algorithms include a heuristic function $h(n)$ as a component of $f$. 
	- $h(n)$ is some estimated cost of the cheapest path from the state at node $n$ to a goal state.
	- $h(n)$ takes on many forms, but has the constraint that if $n$ is a goal node, then $h(n) = 0$.

### Informed Search Complexities 

| Algorithm  | Complete? | Optimal? | Time Complexity | Space Complexity |
| ---------- | --------- | -------- | --------------- | ---------------- |
| Greedy BFS | No        | No       | O(b^m)          | O(b^m)           |
| A*         | Yes       | Yes**    | Exponential     | O(b^d)           |

### Important Informed Search Descriptions
- Greedy Best-First Search
	- Heuristic $h(n)$ estimates the cost from a node to the goal node.
	- Expands the node that appears closest to the goal.
	- Example: route-finding problem in Romania. 
	- Heuristic = straight line distance $h_{SLD}$
	- ![[distance_screenshot.png]]
	- Expand the nodes with the lowest $h_{SLD}$. 
- A* Search
	- First, look at Uniform-Cost Search (UCS) vs. Greedy Best-First Search (GBFS)
		- GBFS checks how far you are from the goal node.
			- Like with $h_{SLD}$.
		- While UCS tries to keep you closer to the starting node.
			- By picking minimum cost paths from the staring node.
	- A* combines the two approaches with the function $f(n) = g(n) + h(n)$
		- Where $g(n)$ is the cost to reach the node (from UCS), and
		- $h(n)$ is the straight line heuristic (from GBFS).

### Extra Local Search Algorithms

> In optimization problems, the **path to the goal is irrelevant** — the solution *is* the goal state itself. All four algorithms below operate on complete-state formulations.

---

#### Comparison Table

| Property | ⛰️ Hill-Climbing | 🔥 Simulated Annealing | 🔦 Local Beam Search | 🧬 Genetic Algorithms |
|---|---|---|---|---|
| **Category** | Greedy local optimizer | Probabilistic escape artist | Parallel hill-climber | Evolution-inspired optimizer |
| **Core Idea** | Always move to the best neighbouring state; stop when no better neighbour exists | Allow bad moves early (high temp), reduce them over time — like cooling metal | Spread *k* beams across the state space; keep the most promising | Simulate natural selection: fit individuals breed, unfit die out |
| **Key Parameter** | — | Temperature schedule (cooling rate) | Beam width *k* | Population size, crossover rate, mutation rate |
| **Variants** | Steepest-ascent, Stochastic, First-choice, Random-restart | Geometric cooling, Adaptive SA, Parallel SA | Stochastic beam search | Steady-state GA, Elitist GA, NSGA-II, Differential Evolution |
| **Strengths** | Very fast per iteration; O(1) memory; simple to implement | Can escape local maxima; works on non-differentiable spaces; global optimum guaranteed (given enough time) | More robust than single hill-climbing; beams share useful information | Handles large/complex spaces; highly parallelisable; maintains diversity |
| **Weaknesses** | Gets stuck in local maxima; struggles on ridges/plateaus; sensitive to initial state | Slow convergence; sensitive to cooling schedule; no speed guarantee | Beams can cluster (lack diversity); higher memory than hill-climbing | Many hyperparameters to tune; computationally expensive; crossover can destroy good solutions |
| **Time Complexity** | O(∞) worst case | O(∞) worst, O(poly) in practice | O(k × b) per step | O(pop × gen × fitness) |
| **Space Complexity** | O(1) | O(1) | O(k) | O(pop) |
| **Classic Example** | 8-queens: move one queen per column to minimise attacking pairs | VLSI layout: accept worse component placements early to escape poor local optima | 8-queens with k=3: run 3 random boards, always keep the 3 with fewest attacking pairs | 8-queens as string "24748552"; crossover two strings, then randomly flip one digit |
| **Real-World Uses** | Sudoku solvers, job scheduling, network routing | VLSI layout, airline scheduling, protein folding | Speech recognition, LLM beam decoding, machine translation | Circuit design, scheduling, neural architecture search, AI music composition |

---

### Key Notes

- **Hill-Climbing — Random Restart**: Re-running from different starting points is surprisingly effective. The 8-queens problem is solved in just a handful of restarts on average.
- **Simulated Annealing — Formal Guarantee**: If temperature decreases slowly enough, SA *will* converge to the global optimum. The catch: "slowly enough" can be impractically long.
- **Local Beam Search — Modern Relevance**: This is essentially how LLMs perform text decoding. It's one of the most practically important algorithms on this list.
- **Genetic Algorithms — Tuning Complexity**: Population size, crossover rate, mutation rate, and selection pressure all interact. Auto-tuning variants like CMA-ES are often preferred in practice.

---

#### The n-Queens Problem (Running Example)

All four algorithms are commonly demonstrated on the **n-queens problem**: place *n* queens on an *n×n* board such that no two queens attack each other.

- **State space**: all possible placements of *n* queens (one per column)
- **Objective**: minimise the number of attacking pairs
- **Goal state**: zero attacking pairs


### The 8-Puzzle Example
- Need information for some details in this section.

| Property              | Definition & Importance                                                                                       |
| --------------------- | ------------------------------------------------------------------------------------------------------------- |
| Admissible            | h(n) never overestimates the true cost to reach the goal. Required for A* optimality on trees.                |
| Consistent (Monotone) | h(n) <= cost(n, n') + h(n') for every successor n'. Ensures A* optimality on graphs (no re-expansion needed). |
| Dominant Heuristic    | If h1(n) >= h2(n) for all n, h1 dominates h2. A dominant heuristic expands fewer nodes.                       |

- Main idea: goal from a starting state to a final goal state.
- ![[8_puzzle_ex_screenshot.png]]
- Average branching factor = 3 and the average solution for a random puzzle is about 22 steps.
	- So exhaustive tree search is $b^d=3^{22}$ or about $3.1 \times 10^{10}$ states.
		- Reduces to 181,440 distinct states (still large).
	- Therefore, we need heuristics that do not overestimate (known as admissible)
- Two common heuristics:
	- $h_{1}$ = the number of misplaced tiles
		- Simply count the misplaced tiles
		- Admissible heuristic --> clear that any tile that is out of place must be moved at least once
	- $h_{2}$ = the sum of the distances of the tiles from their goal positions
		- Admissible heuristic --> because all any move can do is move on tile one step closer to the goal



# References
