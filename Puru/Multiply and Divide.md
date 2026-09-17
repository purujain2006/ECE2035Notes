
~={red}THESE INSTRUCTIONS DO NOT HAVE IMMEDIATE COUNTERPARTS=~
- SHIFTING FOR MUL, DIVIDING IMMEDIATES.
- ALWAYS NEED REGISTERS

`32-bit` times `32-bit` is `64-bit` ~={red}sometimes=~

**SEPARATE** from lui.

---

Consider 
	- `25 * 10` -> 250
		- Each of these numbers can be comfortable stored in 32 bits. Inputs and the result.
		- `mul x9, x6, x7` stores ~={yellow}LOWER 32 bits of product=~
	- `250*250` -> `62500` 
		- The output ~={red}CANNOT=~ be stored in 32 bits.
		- `mul` TO GET ~={yellow}LOWER 32 bits=~
		- `mulh, mulhu, mulhsu` TO GET~={yellow} UPPER 32 bits=~
			- `mulh` if BOTH sources signed. (sign-extend both inputs)
			- `mulhu` if BOTH sources unsigned. (0-extend both inputs)
			- `mulhsu` if 1st signed, 2nd unsigned. (respective extend)

**Divide**
- `div x9, x6, x7`
- Stored as 32 bit integer

**Remainder/Modulus**
- `rem x9, x6, x7`
- Stored as 32 bit integer

---
