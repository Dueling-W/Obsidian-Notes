
2026-03-10 15:26

Tags: [[machine learning]] [[artificial intelligence]]

# What Are AI Agents?


### Introduction to AI Agents, Agent Function and Program
- An **AI Agent** is anything that can perceive 1) its active environment and 2) act on its perception.
	- Humans can be considered an "agent", where they perceive the environment using ears, eyes, and nose and act on this perception using arms, legs, etc. 
- The agent function is a theoretical description of agent behavior.
- Agent function is defined as: $f: P* \to A$
	- Where $P*$ is the set of all possible percept histories.
	- Percept history --> any input the agent receives from its environment (what does it see, hear, read, etc.)
		- Entire history of perceptions (not just the current environment). 
	- Where $A$ is the set of all possible actions the agent can take.
- The agent program is a concrete implementation of the theoretical function.
	- $\text{agent} = \text{architecture} + \text{program}$
	- Architecture --> physical or computational state: sensors, memory, processors (e.g., a GPU server, a robot body). 
	- Program --> software logic that reads the percepts from the architecture and decides on a particular possible action.
- Key idea: the agent program and agent function separate what the agent should do (the agent function), independently of how it's built (the agent program).
	- This keeps the goal consistent between different possible architectures/programs.
- A rational agent strives to "do the right thing" based on what it perceives and the actions it can take.
	- A performance measure (e.g., time taken, distance traveled) is needed for the agent to define "right".
	- Rationality $\neq$ omniscience 
- Autonomous agents have their behavior determined by experience, letting them learn and adapt over time.

### PEAS Framework
- Used for intelligent agent design.

| **Metric**          | **Description**                                      |
| ------------------- | ---------------------------------------------------- |
| Performance Measure | Defines success                                      |
| Environment         | External factors the agent interacts with            |
| Acuators            | Enable actions (e.g., motors, display speech)        |
| Sensors             | Gather perceptual data (e.g., camera, keyboard, GPS) |

### Environment Types
- Six dimensions that combine to describe any environment an agent is working within.
- An environment gets one label from each following pair.

| Environment Pair                          | Description                                                                                 | Examples                                                                                                                                                                                                                                                                                 |
| ----------------------------------------- | ------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Fully Observable vs. Partially Observable | Can the agent see everything it needs for a decision?                                       | Chess (Fully Observable), both players see the board<br><br>Poker (Partially Observable), can't see opponent's hands                                                                                                                                                                     |
| Deterministic vs. Stochastic              | Given the same state and action, do you always get the same result?                         | Chess (Deterministic), moving pieces is always the same<br><br>Backgammon (Stochastic), a dice roll introduces inherit randomness                                                                                                                                                        |
| Episodic vs. Sequential                   | Does a past decision affect future ones? Or, singular, atomic events vs. continuous         | Spam filter (Episodic), classifying this email as spam doesn't affect the next<br><br>Chess (Sequential), each new move shapes the possible futures of the game                                                                                                                          |
| Static vs. Dynamic                        | Does the environment change while the agent is thinking?                                    | Crossword puzzle (Static), the puzzles remains the same while thinking<br><br>Taxi driving (Dynamic), traffic + overall environment is changing always<br><br>Chess with clock (Semi), the environment (board state) stays the same, but slower moves can lose the game/run out of clock |
| Discrete vs. Continuous                   | Are the states and actions countable and distinct, or fluid? Compares number of "states"    | Chess (Discrete), has a discrete set of board states<br><br>Taxi Driving (Continuous), infinite state environment - position, speed, steering, etc.                                                                                                                                      |
| Single Agent vs. Multi-Agent              | Is the agent operating alone, or are there other agents whose behavior it must account for? | Crossword Bot (Single Agent), just an agent working on solving a crossword<br><br>Soccer Robots (Multi-Agent), working together (or against other agents) in a competitive sport                                                                                                         |

### AI Agent Types

| **Agent Type**               | **Main Strength**                                           | **Limitations**                                      | **Best For**                                     | **Example**                    |
| ---------------------------- | ----------------------------------------------------------- | ---------------------------------------------------- | ------------------------------------------------ | ------------------------------ |
| **Simple Reflex Agent**      | Instant reaction based on fixed rules                       | No memory or learning; fails in dynamic environments | Fully observable, stable and simple environments | Traffic light timers           |
| **Model-Based Reflex Agent** | Handles partial observability with internal state           | More computational demand; depends on model accuracy | Dynamic or partially observable environments     | Robot vacuum cleaners          |
| **Goal-Based Agent**         | Plans ahead to achieve specific objectives                  | Needs clear goals and planning algorithms            | Strategic tasks with defined goals               | Logistics route planning       |
| **Utility-Based Agent**      | Balances multiple factors for best outcome                  | Requires complex utility functions                   | Multi-criteria decision-making                   | Financial portfolio management |
| **Learning Agent**           | Improves over time via experience                           | Needs data and training time                         | Dynamic environments with changing conditions    | AI chatbots                    |
| **Multi-Agent System (MAS)** | Distributed problem-solving with cooperation or competition | Complex interactions; unpredictable behaviors        | Decentralized, multi-entity systems              | Smart traffic control          |
| **Hierarchical Agent**       | Breaks complex tasks into levels for efficiency             | Requires well-defined interfaces between layers      | Large-scale, multi-level operations              | Drone delivery management      |





# References
- [[Week 2 - Introduction to AI Agents]]