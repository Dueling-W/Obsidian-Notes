2026-09-24 17:01

Course: #cis570 

## Big Ideas

*quick summary of ideas - 3-5 bullet points max*

## Key Concepts

*place links to full notes here*

## Notes
- Instruction formats
	- J-format: used for j and jal
	- I-format: used for instructions with immediate nums
	- R-format: used for all other instructions
- More fields for R-format
	- rs --> source register
	- rt --> target register
	- rd --> destination register
	- opcode + funct specify the full instruction set
	- shamnt --> shift amount
- Solution to problem of too large numbers: translate into multiple instructions
	- The original is called a "pseudo" instruction
	- lui --> loads the upper half (ABAB) into $at
	- ori --> combines the upper half ABAB with CDCD, resulting in the full 32-bit number being stored into
- 

## Questions/Gaps/Concerns



## Follow-up 

*actions items to follow-up on (e.g., watch video, re-read notes, hw)*



## References

*link to other notes, attachments, or actual lecture slides*
