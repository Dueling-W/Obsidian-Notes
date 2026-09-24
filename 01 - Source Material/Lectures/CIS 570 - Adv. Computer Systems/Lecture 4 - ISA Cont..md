2026-09-15 17:06

Course: #cis570

## Big Ideas

*quick summary of ideas - 3-5 bullet points max*
- Two ways of execution --> sequential model (Von Neumann) vs. dataflow
- 
## Key Concepts

*place links to full notes here*

## Notes
- Instruction specifies who receives the result and fires when all operands are available
	- I.e., as soon as ARG 1 and ARG 2 are available, the instruction is executed
- Sequential is much slower because of the movement of data between registers (store here, re-load here, etc etc)
- Major data flow nodes --> conditional, relational, barrier synch
- Best case --> program counter for ISA (programmer can track execution and logic) and no program counter for micro-architecture (maximize the performance)
- Preserve the semantics for execution order of instructions
	- Ref. slide 25 for a more detailed breakdown of the positives
- Lots of details/questions to ask about a statement
	- Such as available operations, operands, referencing, etc.
- Designing fast ISA (ref. slide 32)
	- Fast fetch, decode, and execute
	- Ex: fast execution --> optimize the common case
		- Such as matrix multiplication for an AI system

## Questions/Gaps/Concerns



## Follow-up 

*actions items to follow-up on (e.g., watch video, re-read notes, hw)*



## References

*link to other notes, attachments, or actual lecture slides*
- [[Lec02_ISA-570.pdf]]