
---

`( a + b ) << ( c - 35 )`

~={green}**operators**=~
	 `+`, `<<`, `-`

~={green}**operands**=~
	`a`, `b`, `c`, `35`

**ex:**
	`a=5`, `b=2`, `c=37`
	7 << 2 
	 LEFT shift BINARY value of 7 by 2 bits.


	 000111 << 2


	 a = x5
	 b = x6
	 c = x7
	 

**SLL** vs. **SLLI**  --> Shift by value in register (variable) vs. Shift by constant value
**SLA**     **SLAI**

right: `>>>`, `>>` depending on language
left: `<<` Logical left and right are the same.

```riscv
add    x9, x5, x6
addi  x10, x7, -35
sll   x11, x9, x10 
```

---


**ALL COMPUTATIONS ONLY INVOLVE REGISTER/IMMEDIATE VALUES**
Data can come from immediates and memory accesses.

>[!warning]
**IMPORTANT:**
Immediate values have their range dictated by *Instruction Format*

Remember, each RISC-V instruction is 32-bits and the kind of instruction dictates the number of bytes each field gets. Example, I and S/B instruction types have 12 bits, so 2^12 values 

- unsigned -> 0 to 2^12 
- signed 2's complement -> -2048 to 2047

12 bits, signed is the **typical immediate value**

>[!important]
>If `C` Code has constant OUTSIDE -2048->2047, need multiple instructions to implement in RISC-V

basic logical operators are all BITWISE.

---

**BOOLEAN ALGEBRA

- Single bit (0/1) works as intended, returning 0/1
- Multiple-bit values work bitwise, and there's no truth-i-ness to such values
- *Typically implemented via branching*

---
 #Memory

~={red}**Memory Data**=~ can only be put into registers through LOAD Instruction.

Location is Immediate + Register's Value

```riscv
lw x5, 1000(x0) 
```
![[Pasted image 20260830171553.png]]

Notice how we can read the value from a different register AS a memory value.

---

~={yellow}LOAD =~

![[Pasted image 20260830175004.png]]
// if MEM:1004 is 55, store 55

---

~={yellow}STORE=~

"store word"
```riscv
sw Rs1, Immed(Rs2)
```

Write Rs1 to Memory address (Rs(2).val + immediate)
![[Pasted image 20260830175212.png]]
![[Pasted image 20260830175327.png|583]]

>[!important]
>`4000(x0)` does not FIT 12-bit signed. 
**DISPLACEMENT (IMMEDIATE VALUE) MUST BE 12-BIT FIELD**


---

~={blue}WORDS=~

![[Pasted image 20260830175514.png]]

A "word" is 4 bytes (32 bits). 

`1000` -> B1, B2, B3, B4
`1004` -> B5, ...

Address is the byte-#/address of the first word.