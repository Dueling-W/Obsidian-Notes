2026-10-15 17:04

Course: #cis570 

## Big Ideas

*quick summary of ideas - 3-5 bullet points max*

## Key Concepts

*place links to full notes here*

## Notes
- Data path summary --> based on data transfers required to perform instructions
- There are logical decisions in the datapath, need the controller to cause the right actions to happen
	- E.g., --> want the controller to instruct the ALU to perform the subtract instruction
- Cycle needs to accommodate the longest instruction (plus a small buffer time)
	- Load instruction needs the entire datapath (longest)
	- Wasting clock period
- Two aspects: clock period (duration) and frequency (cycles per second)
	- Of course, period is 1/frequency
- Multi-cycle implementation
	- Only one stage of instruction per clock cycle
	- Can skip unused stages in a particular instruction or pipelining instructions 
	- Problem --> program counter is incremented on every clock cycle, but they are now very short!
	- This means that the instruction will just get overwritten
- Multi cycle datapath with multiplexors (on slide 44)
- 100 ns to 110 ns when swapping from single to multi
	- Because of all the added extra steps (such as with the IR and MDR) stages
- 


## Questions/Gaps/Concerns



## Follow-up 

*actions items to follow-up on (e.g., watch video, re-read notes, hw)*



## References

*link to other notes, attachments, or actual lecture slides*
