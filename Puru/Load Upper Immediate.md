
**Gets larger constants into registers.**

**GOOD TO KNOW:**
[[Hexadecimal]]

**~={red} MISCONCEPTIONS=~**
- `addi` DOES NOT JUST ADD STRAIGHT DOWN. **~={yellow} UNSIGNED=~**
- **Not necessarily JUST 0,1 => 1 ** REMEMBER CARRIES.
- Better to remember important numbers like -1, etc.

![[Pasted image 20260903183651.png]]

- **Max value:**
	- ~={red}unsigned:=~ `4096` || `0xFFF`
	- ~={green}signed: =~`-2048, 2047` || `0x800, 0x7FF`
		- ~={green}Remember, converting to higher bits for signed => sign-extend=~
		- `0x800` => `0xF800`

---

~={yellow}**How do we put `0xABCDE612` into register?** =~

~={cyan}NOTICE: value fits into 32 bits.=~
- **Issue is INSTRUCTIONS only send 12-bits,  it is NOT the value. **
	- `addi x5, x0, 0xABCDE612`
	- Stores `0x00000612` (bottom 12-bits)

**Load Upper Immediate** is ~={pink}U-Type=~ Instruction.
- We can send 20 bits. 
	- `lui x5, 0xABCDE`
	-  Stores `0xABCDE000` 

**~={green} Answer: lui + addi=~**
- `lui x5, 0xABCDE`
- `addi x5, x5, 0x612`

---

**Negative Caveat**

- ~={red} The lower 12-bit portion CAN BE NEGATIVE.=~ **addi** yields wrong result.

![[Pasted image 20260903191553.png]]

- Sign extension causes -1 (the `111111...`) to be added to upper 20 bits.
	- Remember, that consistent 1s in **signed** is -1.
- ~={yellow} ADD 1 TO THE UPPER-20 bit immediate value=~
	- If you WANTED the upper 20-bit to be `0xABCDE` => `lui 0x5, 0xABCDF`
