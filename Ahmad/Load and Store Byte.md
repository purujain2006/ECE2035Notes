![[Pasted image 20260903194308.png]]


~={red}REMEMBER, AN OFFSET IS A 1 BYTE OFFSET=~
- 1 byte skips 2 hex letters, not 1. **memory addressing**

**Byte Ordering**

`0xAABBCCDD`

**The way you see it is different than what might be stored**
- ~={green}RISC-V can be configured to either, but emulator is=~ little-endian

~={red}Little Endian=~ => word address gives LSB
~={orange}Big Endian=~ => word address gives MSB

![[Pasted image 20260903194407.png]]