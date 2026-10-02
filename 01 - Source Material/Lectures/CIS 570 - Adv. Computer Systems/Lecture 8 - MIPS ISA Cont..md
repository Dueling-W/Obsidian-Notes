2026-10-01 17:04

Course: #cis570 

## Big Ideas

*quick summary of ideas - 3-5 bullet points max*

## Key Concepts

*place links to full notes here*

## Notes
- Don't use $at register since it may be used by the assembler
- Example pseudo instruction (slide 69)
	- Rotate right instruction
	- `ror   reg, value`
	- Expands:
	- ```
	  srl $at, reg, value    #shift right by the value (red part)
	  sll reg, reg, 32-value   #shift left by 32-value (the rest)
	  or reg, reg, $at    # or works because shift sets things to 0
	  ```
- TAL (True Assembly Language) --> instructions get translated directly into 32-bit machine code
- Arrays in MIPS
	- `g = h + A[5]`, where g is $s1
	- Used load with a shift amount of 20 --> put that result in a temporary register
	- 20 because each element of the int array is 4 bytes
- Shortcut --> use sll to multiply by powers of 2
## Questions/Gaps/Concerns



## Follow-up 

*actions items to follow-up on (e.g., watch video, re-read notes, hw)*
- Install MARS MIPS assembler
	- Install Java first (will require me to reboot after installation)


## References

*link to other notes, attachments, or actual lecture slides*
