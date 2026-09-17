---

---
---

**Boils down to:**

~={green}Initialization=~
~={red}Test=~
~={cyan}Body=~
~={pink}Update=~

---

`while` loop in C

```c
int M[] = {1, 3, 4, 5, 6, 5, 1, 20, 3, 7, 1} // Assume 100 values.


//initialization
int x = 5;
int i = 0;
int sum = 0;

while (i != 100) { // test
	
	// body
	if (M[i] == x) {
		sum++;
	}
	
	i++; // update
	
}
```


`while` loop in RISC-V

> [!important]
> `slli` by 2 = multiplying by 4


```riscv
.data
	
M:	.word 1, 3 , 4, ... //100 values

.text
	# x5: x
	# x6: i
	# x7: sum
	# x9: loop limit (100)
	# x10: M[i]
	# x11: offset from base address of M (4*i)
	
		  addi x5, x0, 5 // x = 0
		  addi x6, x0, 0 // i = 0
		  addi x7, x0, 0 // sum = 0
	      addi x9, x0, 100 // M.length = 100
	
MLoop:    beq x6, x9, Leave // if x6 = x9, jump to Leave
		
		  slli x11, x6, 2 // scale i to be the word offset (i*4 is word offset)
		  add x11, x11, gp
		  lw x10, M(x11) // read M
		  addi x7, x7, 1 # inc sum
SkipSum:  addi x6, x6, 1 # inc i
		  jal x0, MLoop # loop back
Leave:    jalr zero, ra, 0 # return to OS
	
```


**Optimizing**

- ~={yellow}Using i as actual memory address=~

```riscv
.data
	
M:	.word 1, 3 , 4, ... //100 values

.text
	# x5: x
	# x6: i*4 //offset into array
	# x7: sum
	# x9: loop limit (4*100)
	# x10: M[i]
	
		  addi x5, x0, 5 // x = 0
		  addi x6, gp, 0 // i = gp
		  addi x7, x0, 0 // sum = 0
	      addi x9, gp, 400 // Limit = gp + 100*4

MLoop:    beq x6, x9, Leave // if i*4 = gp + 4*100, exit loop
		
		  lw x10, M(x6) // read M[i] // NOTE: NOT MEMORY ADDR (x6)
		  addi x7, x7, 1 # inc sum
		  
SkipSum:  addi x6, x6, 4 # inc i*4
		  jal x0, MLoop # loop back
		  
Leave:    jalr zero, ra, 0 # return to OS
	
```

>[!warning] `do { body } while (condition)`
>![[Pasted image 20260917195154.png]]

---


**For Loops**

- `bge` rather than `beq`

```riscv
		# x5: x
		# x6: 4*i/offset into array
		# x7: sum
		# x10: M[i]
		 addi x5, x0, 5 # x = 5
		 addi x6, gp, 0 # i = gp
		 addi x7, x0, 0 # sum = 0
		 addi x9, gp, 400 # Loop limit = gp + 100*4
MLoop:   bge x6, x9, Leave # if i*4 >= 400, exit loop
		 lw x10, M(x6) # read M[i]
		 bne x10, x5, SkipSum # if M[i] != x, don't inc sum
		 addi x7, x7, 1 # inc sum
SkipSum: addi x6, x6, 4 # inc i*4
		 jal x0, MLoop # loop back
Leave:   jalr zero, ra, 0 # return to OS
```


---

