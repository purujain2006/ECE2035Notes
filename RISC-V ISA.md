![[Pasted image 20260825164439.png|700]]
![[Pasted image 20260825170119.png]]

---

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

~={yellow}**Add**=~

**RISC-V add always takes 3 operands**
```
<OPCODE> <OUTPUT REG> <INPUT REG>
```
- Fails to add CONSTANTS.

***

~={yellow}**Add Immediate**=~

- RISC-V only allows one ~={red}**Immediate Value**=~ per instruction.
- "CONSTANT"
```
addi x1, x3, 5
```

---

**Reading Memory**

~={yellow}**Load Word**=~

- Read memory, store in register
```asm
lw x1, 0(x3)
```

- `5(x0)` read from register 0, add 5.
- `0(x5)` read from register 5, add 0.

```asm
  <opcode> <outputreg> <immediate value>(<register>)
```

---

**Zeroing a Register**
```asm
sub x11, x11, x11
```

```asm
xor x14,x14,x14
```

---

~={red}**Registers**=~ - 32 General Purpose... but.

`x0` ~={red}**ALWAYS 0**=~ => CANNOT change it.
`x1` **return address**
`x2` **stack pointer**
`x3` **global pointer**
`x4` **thread pointer**
`x8` **frame pointer**

**By Convention.**

---

~={yellow}**Shift Right Arithmetic**=~

- SU EN =1
- ST = 0
- IM VA = 4
- IM EN = 1

Shift Right Arithmetic Immediate.
```
SRAI x6, x5, 4
```

x6 = output
x5 = read
4 = shift

---

~={yellow}**Shift Left Logical Immediate** =~

 `IM EN` = 1
 `IM VA` = -4
 `SU EN` = 1
 `ST` = 0

```
SLLI x6, x5, 4
```

---

Other Instructions 
[[RISC-V_ISA.pdf]]

---

![[Pasted image 20260827163512.png]]

---

RISC-V as different types of instruction formats/fields sizes
Allocates bits for each field. 

- **R** — three registers, no constant. Two sources, one destination. `xor x5, x6, x7`.
- **I** — one source register plus a 12-bit constant. Covers arithmetic-with-immediate _and_ loads, since `lw x1, 8(x3)` is structurally the same shape: one register, one small offset.
- **S** — two registers and a constant, but _no destination register_. Stores read two values and write memory, so the bits that would be `rd` get reused as more immediate bits.
- **B** — same shape as S (two sources, a constant, nothing written back), just with the immediate encoded to point at a branch target.
- **U** — one destination and a big 20-bit constant, no source register.
- **J** — one destination and a big 20-bit target.

---
