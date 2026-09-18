
---

~={yellow}**1D Arrays**=~

```c
int A[3] = {11, 22, 33};
```

-  ![[Pasted image 20260917202926.png]]

---

~={yellow}**2D Arrays**=~

```c
//   Ly  Lx
int A[4][3] = { 
				{ 0 ,  1,  2 }
				{ 3 ,  4,  5 }
				{ 6 ,  7,  8 }
				{ 9 , 10, 11 }
				}
```

- ~={purple}`Ly` rows=~
- ~={blue}`Lx` columns=~

	- ![[Pasted image 20260917204935.png|327]]

> [!important] 
> **Row-major Order**
> - Rows are stored ~={yellow}contiguously=~; 

---

~={yellow}**Effective Address**=~ (Calculating Memory Offset)

- ~={purple}**Types**=~ take different space in memory

```c
		int x = A[r][c];
		double x = A[r][c];
```

- n-D arrays ~={red}MUST=~ store arrays of the same size in each added dimension/"row".
---

$$
\large
\texttt{type}\; x
=
A[{\color{#22c55e} row}]
[{\color{#f59e0b} columns}]
$$

$$
\large
\text{Effective Address}
=
\text{Base}
+
\bigl(
{\color{skyblue} Lx} \cdot {\color{#22c55e} r}
+
{\color{#f59e0b} c}
\bigr)
\cdot
\lvert \texttt{type} \rvert
$$

- `Lx * r` skips you directly to index `[0]` of row `r`
- `+ c` offsets you by index

---
---

**~={yellow}Indices FROM Effective Address=~**

- Effective Address: `3224`
- Width x Height = 64x64
- `row` = `floor ( 3224/64 )`
- `column` = `3224 % 64` 

---

**3D Arrays**


![[Pasted image 20260917211828.png|290]]
![[Pasted image 20260917211806.png|294]]
![[Pasted image 20260917212024.png|362]]

---

~={yellow}**Effective Address**=~ (Calculating Memory Offset)

$$
\large
\texttt{type}\; x
=
A[{\color{gray} planes}][{\color{#22c55e} row}]
[{\color{#f59e0b} columns}]
$$

$$
\large
\text{Effective Address}
=
\text{Base}
+
\bigl(
{\color{violet} Ly} \cdot {\color{skyblue} Lx} \cdot {\color{gray} p}
+
{\color{skyblue} Lx} \cdot {\color{#22c55e} r}
+
{\color{#f59e0b} c}
\bigr)
\cdot
\lvert \texttt{type} \rvert
$$

- `Ly * Lx * p` skips you to index `[0][0]` of plane `p`
- `Lx * r` skips you directly to index `[0]` of row `r`
- `+ c` offsets you by index

---
---

**~={yellow}Indices FROM Effective Address=~**

- Effective Address: `3224`
- Width x Height = 64x64x64

- `plane` = `floor ( 3224/(64*64) )`
- `row` = `floor ( 3224/64 )`
- `column` = `3224 % 64` 

---
**Generically**

![[Pasted image 20260917212811.png]]

---

