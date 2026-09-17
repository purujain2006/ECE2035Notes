
**Two names referring to the same thing**

`x0` or `zero` -> zero address
`x1` or `ra`     -> return address
`x2` or `sp`     -> stack pointer
`x3` or `gp`     -> ~={red}global pointer=~
`x4` or `tp`     -> thread pointer
`x8` or `fp`     -> frame pointer

---

~={yellow}**Static Memory**=~

- `gp` or global pointer is the BASE ADDRESS of this region.

- global variables
- program instructions

- memory there when program starts, removed when it ends.

---

~={orange}**.data**=~
- Corresponds to global variable declaration

~={orange}**.text**=~
- Corresponds to program instruction declaration

~={orange}**.word =~`<init value>` , `<init value>` ...**
- do not NEED to give a name, ANP, VetName, etc.
- `.word 5, 17` allocates 2 words consecutively.
	- `P: .word 25, 17` --> assume P = 2000.
	- `2000: 25`
	- `2004: 17`
- Can only allocate `4 bytes` and values up from `-2048 - 2047`.
	- `double word` for larger values, etc.

**~={orange}.alloc=~ `<bytes>` **
- Allocate uninitialized bytes


---

**Example Program**

```riscv
.data
ANP:      .word 5
VetName:  .alloc 4

.text
main: lw   x7, ANP(gp)
      addi x6, x7, 4   
```

~={green}**Process**=~

- **ANP** is an **address** leading to a WORD (4 bytes) holding value 5.
- **VetName** is an **address** leading to 4 uninitialized bytes.

- Note that address is RELATIVE where it's allocated.

- Allocate ANP (offset 0 from gp)
- Allocate VetName (offset 4 bytes from gp (bc ANP), 4 bytes)
- Load `ANP` into reg x7.
- Add 4 to reg 7, store in 6.

---

~={blue}**Absolute Addresses**=~
- adding new global variable changes memory jumps
	- `lw x6, 8(gp)` may point correctly until something inserted, pushing value we want to `12(gp)`

~={blue}**Labels** =~
- The value of a label is the address where it is defined, relative to `gp`.
- `ANP: .word 5` 
- **ANP** is a mnemonic representing offset from `gp`.

---

`jalr zero, ra, 0` ends program by handing control back to operating system.