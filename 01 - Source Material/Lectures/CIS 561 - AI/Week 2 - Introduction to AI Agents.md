## References
- [AI Agent Overview](https://canvas.umassd.edu/courses/20990/pages/intelligent-agents?module_item_id=1339478)
- [Types of Agents Article](https://www.geeksforgeeks.org/artificial-intelligence/types-of-agents-in-ai/)
- [Understanding AI Agents Video](https://www.youtube.com/watch?v=zpKLxKsJ9oE)

## AI Agent Overview
- Agent --> anything that can perceive its environment and act on its perception 
	- Human agent --> uses eyes, ears, etc. for sensors and uses hands, arms as actuators to act on sensed info.
	- Robot agent --> cameras, sensors, uses various motors for actuators
- Agent function
	- Abstraction/theoretical description of agent behavior
	- Maps percept histories to actual actions
		- Percept history --> any input the agent receives from its environment (what does it see, hear, read, etc.)
	- The function: $f: P* \to A$
		- Where $P*$ is the set of all possible percept histories
		- A --> set of all possible actions the agent can take (move its arm, output text, etc.)
	- Key insight: agent's decision is based on its entire history of perceptions, not just what is currently going on
		- Important because the past greatly matters
- The agent program
	- Concrete implementation of the theoretical function
		- $\text{agent} = \text{architecture} + \text{program}$
		- Architecture --> physical or computational state: sensors, memory, processors (e.g., a GPU server, a robot body)
		- Program --> software logic that reads the percepts and decides on a particular possible action
- Together, the agent program and agent function helps separate what the agent *should* do independently of *how* it's built
- Rational agent
	- Strives to "do the right thing" based on what it perceives and the actions it can take
	- Need a performance measure for the agent to define "right", e.g., dirt cleaned, time taken, for a vacuum-cleaner agent
	- For each possible percept sequence, a rational agent selects an action expected to maximize performance, given the evidence and built-in knowledge.
	- Rationality doesn't necessarily mean omniscience
	- Autonomous agents --> behavior determined by experience, has the ability to learn and adapt
- PEAS Framework for intelligent agent design

| **Metric**          | **Description**                           |
| ------------------- | ----------------------------------------- |
| Performance Measure | Defines success                           |
| Environment         | External factors the agent interacts with |
| Acuators            | Enable actions                            |
| Sensors             | Gather perceptual data                    |
- Environment types
	- Fully observable vs. partially observable
		- Complete state of environment available vs. not
	- Deterministic vs. stochastic
		- Determined by current state and action vs. random elements.
	- Episodic vs. Sequential: Divided into atomic episodes vs. continuous.  
    - Static vs. Dynamic: Environment unchanged during deliberation vs. changing.  
    - Discrete vs. Continuous: Limited distinct states vs. infinite states.  
    - Single Agent vs. Multi-Agent: Solo agent vs. interactions with other agents.

## AI Agent Types
- Simple Reflex Agents
	- Purely react to inputs without consideration for prior events or predicting future outcomes
	- Excel in predictable environments with straightforward tasks
	- Quick response time since decisions are made based on immediate input
	- Cannot improve or change their behavior bast on past experiences
- Model-Based Reflex Agents
	- Mental model of their environment
		- Playing out various scenarios
	- Internal state allows the agents to handle scenarios where some aspects are not directly observable
	- They update their internal model based on new information
	- Helps these agents make better decisions by referring to their internal model (minimizes impulse or suboptimal choices)
	- Increased computational demands because they need to maintain their internal model
- Goal-Based Agents
	- They are given explicit goals and make their decision based on how their actions align with these objectives
	- Often using planning algorithms that explore multiple possible actions, thus finding the most effective sequence of steps that lead to their goal
	- These agents can re-plan/adjust if new information arises (flexibility)
	- They think ahead and predict future outcomes to find the best course of action for their goal
- Utility-Based Agents
	- Agents factor in things like cost, benefits, risk, time, etc. to find the best course of action
	- Can balance competing goals and preferences, often finding the best "compromise"
	- More adjustable to subjective preferences or goals
	- Increased complexity since finding the necessary utility functions for different factors can be computationally intensive and complex
- Learning Agents
	- These agents receive continuous feedback from their actions
	- Learning agents are able to both explore (find new actions) and exploit known successful strategies
	- They modify their behavior based on new incoming data
	- It can apply the lessons they learned in one context to a new, similar situation (enhanced versatility)
- Multi-agent system (MAS)
	- Operate in environments with other agents, cooperating or competing to achieve individual or group goals
- Hierarchical agents
	- Organize behavior into multiple layers
	- High layers make abstract decisions that break down into more specific subgoals for the lower level agents to execute