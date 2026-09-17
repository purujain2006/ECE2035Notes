
---

**Arithmetic Shifting**
- ~={red} Left=~   pad LSB with 0.
	- Use `slli` (same as arithmetic)
- ~={yellow} Right=~ pad MSB with MSB. 
	- above for signed. 
	- 0 for unsigned.

**Logical**
- ~={red}Left=~  pad LSB with 0. 
- ~={yellow}Right=~ pad MSB with 0.

>[!important]
>**Left Shift** by n   => multiplying 2^n
>**Arithmetic Right Shift** by n => dividing 2^n
>- ~={yellow}Applies to Right Shift for Two's Complement (signed)=~


**Rotate is NOT supported by RISC-V**

---

~={cyan}**I-Type=~ Shift Instructions**
- Immediates
- `slli` - left logical immediate + left arithmetic immediate
- `srli` - right logical immediate
- `srai` - right arithmetic immediate

**~={green}R-Type=~ Shift Instructions**
- ~={red}Supply Registers=~
- `sll, srl, sra`

---

Compiler looks at **TYPES** when deciding what `>>` means
- `srli` for unsigned integers. 
	- ~={orange}logical is signed-independent=~
- `srai` for integers (default signed)

---


