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

```riscv
.data
	.word 1, 3 , 4, ... //100 values

.text
	# x5: x
	# x6: i
	# x7: sum
	# x9: loop limit (100)
	# x10: M[i]
	# x11: offset from base address of M (4*i)
	
	addi x5, x0, 5 
	addi x6, x0, 0 
	addi x7, x0, 0
	addi x9, x0, 100
	
	
	
```