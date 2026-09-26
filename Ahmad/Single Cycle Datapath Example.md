	![[Pasted image 20260827153928.png]]

---
In single-clock cycle, two registers read, one written.

~={yellow}XYZ=~ = signals from ~={red}*CONTROL MODULE*=~ that dictate 
- what registers are involved.

~={green}**Register** =~
- 32x32 => 32 registers, each storing values up to 32 (5 bits).
- **5** => # of bits supplied to register file.
- 5 bits = 0-31 => 32 values. (specifying)

---

~={orange}**RWE** =~
- **read/write** 
- This operation ~={red}WILL write=~ to register, storing in Z.

**Inputs**
X (reg 5) 
Y (reg 7)

**Output**
Z (reg 6)

---

~={red}*Only 1 ENABLED*=~
- ALU

--- 
~={orange}**AU EN**=~

 - **Arithmetic Unit** 
- ~={yellow}**S/~A**=~
	- Subtract/NOT Add.
	- if 1, AU subtracts.
---

~={orange}**LU EN**=~

- **Logic Unit**
- ~={yellow}**LF**=~
	- 6 => XOR

---
~={orange}**SU EN**=~

- **Shift Unit**
- ~={yellow}**ST**=~

	- 0=logical
	- 1=arithmetic
	- 2=rotate
	
- ~={yellow} **IM VA**=~
	-~={red} + = right=~
	-~={red} - = left=~
	
---

~={orange}**M SEL**=~

- Memory Select

~={orange}**ST EN**=~

- Store Enabled

~={orange}**LD EN**=~

- Load Enabled

~={orange}**R/~W**=~

- Read/Write memory

****

~={orange}**IM VA**=~

- Sign Extender.
	- Extend MSB leftward. "sign" extended.
	- enabled for ALL **ALU** immediate operators (addi/xori/slli, etc.)
		- 1110 => 1111 1110
		- 0110 => 0000 0110
- Takes in **A VALUE**  with different amount of bits, returns same value in bits required by processor. 
	- Specifies SHIFT by ___ bits.
	- If `IM VA` =  4, shift by 4.  + = right. 
	- If `IM VA` = -4, shift by 4. -  = right
- 0X123 (12 bits) -> 0x0...123 (32 bits)

---

**Assembly Equivalent**
```asm
SUB x6,x5,x7
```

[[RISC-V ISA]]

REMINDER:

