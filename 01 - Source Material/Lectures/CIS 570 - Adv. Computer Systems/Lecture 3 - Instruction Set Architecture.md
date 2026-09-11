2026-09-10 16:57

Course: #cis570

## Big Ideas

*quick summary of ideas - 3-5 bullet points max*

## Key Concepts

*place links to full notes here*

## Notes
- Quiz next week --> covering lecture 1 (execution cycle overview)
- Helpful walk-through of instruction execution at end of Lec01 slides (pgs. 17-20)
- Computing is layers/levels of abstraction going from a problem --> electrons themselves
- Even hardware is separated in micro/macro levels
	- Micro --> transistors, logic gates, etc.
	- Macro --> processor, PCBs, mobile telephones, PCS, etc.
- ISA vs. Microarchitecture
	- ISA --> instructions to be executed in an order (semantics)
	- Microarchitecture --> specifies how the underlying implementation actually executes instructions
- ISA vs. micro-arch
	- ISA --> acceleration pedal 
	- uarch --> internals of the engine, how to implement "acceleration"
- ISA vs. microarchitecture summary
	- ISA --> agreed upon interface between software and hardware
		- Focused on --> specifying instructions and what they do
	- Microarchitecture --> specific implementation of an ISA
		- Anything done in the hardware without exposure to software
		- Pipelining, speculative execution, etc.
	- Micoprocessor --> combines the two
- 
## Questions/Gaps/Concerns
- If you are optimizing your code, do you just make a better algorithm, or do you optimize for the ISA/microarchitecture?
	- E.g., PyTorch making an efficient/fast matrix multiplication, do they consider an underlying ISA/microarchitecture


## Follow-up 

*actions items to follow-up on (e.g., watch video, re-read notes, hw)*
- Create Anki flashcards for quiz 1 (pertaining to lecture 1)
- Play around with MARIE simulator --> since this will be the topic of homework 1


## References

*link to other notes, attachments, or actual lecture slides*
- [[Lec01-Execution-570.pdf]]
- [[Lec02_ISA-570.pdf]]
- [MARIE Simulator](https://marie.js.org/)