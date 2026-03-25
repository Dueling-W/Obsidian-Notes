
2026-03-12 15:59

Tags: [[artificial intelligence]] [[logic]]

# Knowledge Bases and Propositional Logic


### KBs and Logic Intro.
- Knowledge bases are a set of sentences in formal language.
	- Takes a declarative approach:
		- Tell the agent what it needs to know.
		- Agent can then ask itself what to do.
- Two levels:
	- Knowledge level --> what does the agent know?
		- E.g., "All tiles with glitter have gold."
		- Purely what the agent knows, no computation, just meaning.
	- Implementation level --> data structures in the knowledge base and algorithms for manipulation.
		- In plain terms: how are the sentences stored and manipulated?
		- E.g., are the sentences stored as string? as binary trees?
		- Wants to put meaning behind what the agent knows.
		- Say the agent says: "there is no Wumpus in tile (1,3)", what algorithm produced that conclusion?
	- Can also think of the behavior above all of them: such as getting the gold, fleeing the Wumpus.
	- Overall can be though of as:
		1) Behavior --> what the agent does.
		2) Knowledge Level --> what the agent knows (as logical sentences).
		3) Implementation Level --> how those sentences are physically represented and processed.
- Overall an agent should:
	- Represent states, actions, etc.
	- Incorporate new percepts.
	- Update its internal representation of the world.
	- Deduce hidden properties of the world.
	- Deduce appropriate actions. 
- Logic: formal languages for representing information so conclusions can be drawn.
	- Syntax: defines the sentence structure. What constitutes a well-formed sentence in the language (structure and grammar). 
	- Semantics: defines the meaning of sentences (is it true or false?).
		- The rules that determine the meaning (truth value) of sentences by relating them to models (the world).

### Wumpus World Example
- A useful example for illustrating agents, knowledge bases, and environments.
	- On a 4x4 grid (typically), where there is a Wumpus (monster), gold, and pits.
	- Agent should try to get gold and kill the Wumpus.
- PEAS of Wumpus World

| Performance                                               | Environment                                                                                                                                             | Actuators                                                    | Sensors                                       |
| --------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------ | --------------------------------------------- |
| Gold +1000<br>Death -1000<br>-1 per step<br>-10 for arrow | Adjacent to Wumpus: smelly<br>Adjacent to a pit: breezy<br>Glitter: gold in the square<br>Shooting: kills Wumpus if facing it<br>Can grab and drop gold | Left turn<br>Right Turn<br>Forward<br>Grab, Release<br>Shoot | Stench<br>Breeze<br>Glitter<br>Bump<br>Scream |
- Description of Wumpus World Environment
	- Fully Observable or Partially Observable: Partially Observable (local perception)
	- Deterministic or Stochastic: Deterministic (outcomes are exactly specified, no randomness)
	- Episodic or Sequential: Sequential (current decisions influence future outcomes)
	- Discrete or Continuous: Discrete (countable amount of actions/tiles)
	- Single or Multi-Agent: Single Agent

### Propositional Logic
- Goal is to illustrate basic ideas.
	- Syntax: sentence structure
		- Propositional symbol: variable used to represent something T/F (like "It is raining")
			- Needs to be True/False, cannot be "What time is it?" or use undefined variables.
		- Logical operators:
			- ![[Propositional-logic.png]]
	- Semantics: assigns truth values to symbols in models.
		- So you might want to evaluate if $A \land B$ is T/F.
- Entailment is saying one thing follows from another.
	- A knowledge base entails a sentence if the sentence is true in all worlds where the knowledge base is true. 
- Inference

| Method            | Description                                                                                             | Purpose/Use Case           |
| ----------------- | ------------------------------------------------------------------------------------------------------- | -------------------------- |
| Forward Chaining  | Data-driven: starts from known facts, applies rules to derive new conclusions until query is reached.   | Data-driven and automatic  |
| Backward Chaining | Goal-driven: starts from the query, works backward through rules to find supporting facts in the KB.    | Useful for problem solving |
| Resolution        | Refutation-complete: proves KB \|= alpha by showing KB AND NOT(alpha) is unsatisfiable (contradiction). |                            |
- Pros and Cons of Propositional Logic

| Pros                | Cons                     |
| ------------------- | ------------------------ |
| Declarative         | Limited expressive power |
| Compositional       |                          |
| Context-independent |                          |
# References
