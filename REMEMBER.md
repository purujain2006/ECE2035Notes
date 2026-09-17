
8 BITS IN A BYTE

```riscv
addi a6, gp, Results

#DO NOT USE: 
addi a6, Results, gp

#Third value is an immediate. Second must be register
```


=> while loop

---

SCALING COUNTER FOR MEMORY ACCESS.

i = 1 --> access offset 4
	NEED SLLI by 2

```riscv
.data
.word 1, 2, 
.text

```


OR COULD JUST COUNT += 4

Use x6 for both loop counter (i) and offset into array.

X6 = OFFSET (Pointer)
x9 = LIMIT  (gp + `4*n`)  with n being the number of elements (end of array memory)

initialize i as gp. "Pointer"
read at pointer.
add 4 to i every loop cycle

QUIT when offset = LIMIT

---

for (Initialization; Test; Update){
	Body
}

```c
for(int i = 0; i != 100; i++){
	sum++;
}
```
---

IN C, AN UNDECLARED VARIABLE HAS A RANDOM VALUE (SET BY PREVIOUS VALUE).
IN JAVA, AN UNDECLARED VARIABLE HAS ITS DEFAULT

---

slti = set if less than immediate.
if less than immediate, result register is 1, otherwise, 0 means compared register is greater than or equal immediate

