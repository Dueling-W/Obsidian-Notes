2026-10-20 16:59

Course: #cis570 

## Big Ideas

*quick summary of ideas - 3-5 bullet points max*

## Key Concepts

*place links to full notes here*

## Notes
- **Announcements**
	- Quiz will be next week (10/26) and will cover lecture 3
	- Pop quizzes --> easy stuff covered in lectures, just pay attention in class
- **Examples of stage usage with different instructions**
	- beq only uses three stages (doesn't access memory)
	- What about `sw  R1, R2, 16`
		- Store the value in rt (R1) to Mem\[R2 + 16]
		- Cycles used: 
			- fetch and increment
			- compute a relative address
			- actually do rs + imm16 (sign extended) to compute the effective address (and store in ALUOUT)
			- Mem\[ALUOut] = B, specifiying both the address calculated in ALUOut and the content in register B (rt)
			- Four/five stages used
	- As we know, load uses all five

## Questions/Gaps/Concerns



## Follow-up 

*actions items to follow-up on (e.g., watch video, re-read notes, hw)*



## References

*link to other notes, attachments, or actual lecture slides*
