2026-09-22 17:03

Course: #cis570 

## Big Ideas

*quick summary of ideas - 3-5 bullet points max*

## Key Concepts

*place links to full notes here*

## Notes
- Semantic gap --> distance between high level language and ISA
	- More complicated ISA --> closer to HLL
	- But, this means you need extra/complicated hardware
- Easy example:
	- VAX has assembly instructions for queues, this is very close to HLL but complex for the hardware
- Major parts of memory organization --> address space and addressability (ref. to slide 74 for details)
- Data access support: load/store vs. memory/memory architectures
	- Load/store architecture: only load/store instructions can access memory
		- Arithmetic/logic instructions operate only on registers (or immediate values)
	- Memory/memory architecture: arithmetic/logic instructions can operate on memory locations as well
		- So, memory locations themselves can be in the instructions (address)
- I/O support --> in modern time, memory mapped is more common (i.e., a region of memory is mapped to I/O devices)
- Two main approaches:
	- CISC --> complex instruction set computers
	- RISC --> reduced instruction set computers
- ![[Pasted image 20260922175915.png]]
- $$
\frac{time}{program} = \frac{instructions}{program} \times \frac{cycles}{instruction} \times \frac{time}{cycle}
$$
- Tying it back together to semantic gap
	- CISC has a smaller semantic gap --> closer to the software due to its complex instructions
	- RISC has a larger semantic gap --> it is closer to hardware control signals because of its simple instructions
- 


## Questions/Gaps/Concerns



## Follow-up 

*actions items to follow-up on (e.g., watch video, re-read notes, hw)*



## References

*link to other notes, attachments, or actual lecture slides*
