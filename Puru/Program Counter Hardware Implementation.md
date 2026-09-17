
**Naive View (no branch/jump)**

- Highlighted is "naive" program counter HW.

![[Pasted image 20260908163338.png]]

**Simplification of Single-Cycle Datapath** ALU
![[Pasted image 20260908163141.png]]


 **VIEW THAT SUPPORTS CONDITIONALS + BRANCHING**

 - `pc` must be loaded every clock cycle.
 
- ~={orange}Zero?=~
	- `beq, bne`, the ALU does `rs1 - rs2` => if 0, zero? = 1. 

- ~={yellow}Controller=~
	- **Input:** zero?, opcode
	- **Output**: PCSrc, RWE, etc.
	
	- Depending on opcode and `zero?`,~={red} PCSrc=~ determines whether a jump should be taken.
		- `beq` and `zero? = 1` => jump
		- `bne` and `zero? = 0` => jump
	
- ~={green}Multiplexer Inputs=~
	
	- `pc + 4` is standard for next instruction. Select if no branching/jumping.
		- Also leads to `MemtoReg`, since we can store it in a register.
	
	- `br/jal_pc + offset` is for branching + `jal` jumps. 
		- **Offset** is left shifted by 1 because instructions ALWAYS start at even addresses.
			- RISC-V has 2-byte instructions, so only LS by 1.
			- Use 12-bits for actual information, left shift automatically restores the 0 for even.
			- ~={red}DOUBLES the range =~ -> 2KiB to 4KiB
		- Notice ~={orange}Controller=~ sets `st_en`, but doesn't for `jalr`.
			- branching/`jal` have different storing behaviors, one doesn't store, one does
			- `jalr` always stores
	
	- `jalr_pc_rs + offset`
		- Calculates sum of register value and immediate, store in memory.
		- ~={red}NOT MENTIONED IN CLASS: =~ the LSB is FORCED to 0, since immediate not guaranteed to generate even.
	
 
![[Pasted image 20260908164038.png]]