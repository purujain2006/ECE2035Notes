
~={red}Hexadecimal Character = 4 bits=~
	- `0xFF` = 1 byte/8bits
	- `0xF` = 4 bits
	- `0xFFF` = 12 bits.
	- 

~={yellow}IF HEX VALUE UTILIZES ANY NON-ZERO BIT > 3. HINT TO USE LUI.=~

**Since we know sign depends on the ~={yellow}FIRST bit. (MSB)**=~
- Hex characters = 4 bits.
	- `8 and ALL the letters` as **MSB** => sign-extend 1.
	- `8` = 1000  --> MAX negative. No positive additions (Review 2's complement).
		- `0x8000....` will always be MAX neg.
	- `7` = 0111 --> MAX positive. ALL positive additions, no negative.
		- `0x7FFFF....` will always be MAX pos.
	- `0xF` = 1111 --> Smallest negative, non-zero. (-1)
	
![[Pasted image 20260903185020.png]]
**12-Bits**
![[Pasted image 20260903185136.png]]

**Visualizing Hex Range**
![[Pasted image 20260903184836.png]]