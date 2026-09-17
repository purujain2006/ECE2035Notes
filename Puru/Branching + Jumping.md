
**Program Counter/ Instruction Pointer**
	- Every instruction adds 4 to instruction pointer, except jumps.

~={orange}**Branching:** (if-statement behavior)=~

- ~={pink}**B-type** =~ Instruction
	- LIMITS WHERE YOU CAN BRANCH TO.
	- For, B type, the immediate field stores a ~={red}RELATIVE address.=~
		- Can jump a Max/Min relative amount to `pc` (12-bit immediate)

- `beq` ~={red}jumps to an address when 2 register values are equal=~
	- "Branch equal" `beq` vs. "Branch not equal" `bne`
	- `beq x5, x6, Then`
	- `bne x5, x6, Else`

- ~={cyan}**Instructions**=~
	![[Pasted image 20260908160407.png|646]]

- Modify ~={red}ORDER=~ for greater than, less than equal to, etc.



~={orange}**Jumping Instruction** (JAL)=~

- ~={pink} **J-type**=~ instruction
	-  Range is (+/- 1MB for `jal`)

- `jal` ~={red}writes `pc (program counter) + 4` ~={cyan}(next instruction)=~ to a return address=~, then~={yellow} sets `pc` to the desired address=~
	- `jal x0, End`
		- Sets `pc + 4` to `x0` (Scrapped)
		- `pc` then skips to the instruction at label `END`


- ~={pink} **I-type**=~ Instruction
	- `jalr`  is for larger than `jal` jumps (>20 bits)
	-  `jalr x0, x1, 0x123`

- `jalr` ~={red} writes `pc (program counter) + 4`~={cyan} (next instruction) =~to a return address=~, then~={yellow} sets `pc` to SUM of=~ ~={pink}32-bit register value=~ ~={yellow} and IMMEDIATE value=~


```riscv
.text
	mul x7, x9, x10
	beq x5, x6, Then
	
	
Else: add x11, x12, x13
	  jal x0, End
	
Then: sub x11, x12, x13
	  div x14,  x9, x10
	  
```
