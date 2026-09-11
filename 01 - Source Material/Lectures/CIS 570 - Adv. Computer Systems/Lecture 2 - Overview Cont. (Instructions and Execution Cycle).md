2026-09-08 16:53

Course: #cis570

## Big Ideas

*quick summary of ideas - 3-5 bullet points max*

## Key Concepts

*place links to full notes here*

## Notes
- C program (high level) --> memory
	- Many steps along the way, such as compilation, linkers, and loaders
- Computer system overview
	- Three main blocks --> central processing unit (CPU), input/output system, and memory unit
		- This basic structure is known as the Von Neumann model/architecture
	- CPU --> registers (64-bit in modern time), interface unit, control unit, ALU (ref. 22)
- Instruction cycle: fetch --> decode --> execute
- Microprocessor (instruction cycle)
	- Copy PC to MAR --> copy the contents at address MAR to the IR (instruction register) --> increment PC by 1 --> decode and place bits IR[11-0] in MAR
	- Then, if instruction requires operand --> copy contents of memory at address MAR to MBR
	- If it doesn't requires operand --> execute the instruction
	- Important --> instruction cycle is never interrupted, if the flag is raised, it is addressed *after* the instruction is executed
- MARIE --> Machine Architecture that is really Intuitive and Easy
	- Architecture showing the moving parts of a computer
	- Ref. to below for detailed information
	- ![[Pasted image 20260908180228.png]]
	- Additional info:
		- 16-bit instructions
			- First 4 --> opcode (15-12)
			- Last 12 --> address (11-0)
		- Much, much more detail about MARIE is found [here](http://www.edwardbosworth.com/CPSC2105/Lectures/Slides_05/Chapter_04/MARIE_Organization.htm)
		- Maximum of a single device writing to the common data bus
	- MBR --> Memory Buffer Register
	- Simple explanation of first example:
		1. Load X: MAR <-- X *place address of X in MAR*
		2. MBR <-- M[MAR], *MBR reads address of MAR from bus*
		3. AC <-- MBR, *AC reads the contents from MBR*
	- 


## Questions/Gaps/Concerns



## Follow-up 

*actions items to follow-up on (e.g., watch video, re-read notes, hw)*



## References

*link to other notes, attachments, or actual lecture slides*
- [[Lec01-Execution-570.pdf]]