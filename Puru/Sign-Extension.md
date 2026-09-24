
~={red}ONLY occurs when changing bit-widths=~ ~={yellow}IN MEMORY=~

- `addi` that takes 12-bits in INSTRUCTION, and needs to ADD to 32-bits.

- `0xF` is ~={red}STORED=~ as ~={pink}32-bit=~ `0x 00 00 00 0F`, `0000 ... 0000 0000 0000 1111`
	- IS NOT SIGN-EXTENDED, *~={green}REPRESENTABLE=~* IN 4-bits does ~={red}NOT MEAN=~ it IS 4 bits.