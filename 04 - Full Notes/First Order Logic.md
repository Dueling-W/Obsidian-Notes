
2026-03-12 17:05

Tags: [[artificial intelligence]] [[logic]]

# First Order Logic


### What is FOL?
- FOL introduce to expand on propositional logic, addressing how propositional logic has limited expressive power.
- Assume the world has the following:
	- Objects
	- Relations
	- Functions

| Element     | Description & Example                                                                          |
| ----------- | ---------------------------------------------------------------------------------------------- |
| Constants   | Refer to specific objects. E.g., John, 2, UMASSD                                               |
| Predicates  | Represent relations/properties. E.g., Person(x), Loves(x, y)                                   |
| Functions   | Map objects to objects. E.g., Father(John) = Henry                                             |
| Variables   | Placeholders for objects. E.g., x, y, z                                                        |
| Quantifiers | Universal: forAll x  \|  Existential: exists x                                                 |
| Connectives | Same as propositional logic: AND, OR, NOT, =>, <=>                                             |
| Equality    | Defines equivalence under a given interpretation (siblings defined in terms of shared parents) |
- How can we evaluate truth in FOL?
	- Three major components: model, interpretation, and sentences.
	- Model: the "world" you're evaluating against.
		- Wumpus World --> model contains the actual tiles, the actual Wumpus, the actual gold.
	- Interpretation: mapping that connects formal symbols to real objects in the model.
		- E.g., when you write $Adjacent(x, y)$, which pairs of tiles does that actually hold for?
		- No interpretation --> symbols are just meaningless because they don't connection to the real world model.
	- Truth: just whether or not your sentence checks out.
		- E.g., take $HasGold(tile_{12})$, where the tile is on (1,2)
		- This is true if and only if, after the interpretation maps `tile_1_2` to some actual tile and `HasGold` to the actual "has gold" relation, that tile really does have gold in the model.
- $\forall$ Quantification (Universal)
	- "Everyone in UMASSD is smart" --> applies to all individuals at UMASSD.
- $\exists$ Quantification (Existential)
	- "Some at UMASSD is smart" --> guaranteed to apply to at least one individual at UMASSD.

### Knowledge Engineering in FOL and Applications
- How can agents interact with FOL Knowledge Bases?
	- Telling: adding perceptions or facts to the knowledge base.
	- Asking: querying the knowledge base for answers or actions.
- Knowledge Engineering Steps in FOL
	1. Define the task — what questions should the KB answer?
	2. Assemble relevant knowledge about the domain.
	3. Decide on vocabulary — which predicates, functions, and constants to use.
	4. Encode general and specific knowledge as FOL sentences.
	5. Pose queries to the KB and retrieve answers.
	6. Debug the KB by checking for unexpected answers.
- Applications of FOL include:
	- Wumpus World: uses FOL to deduce hidden properties and formulate reflexes.
	- Electronic Circuits: verifying circuit functionality using logical representations. 


# References
