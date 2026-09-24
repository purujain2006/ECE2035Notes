```c
#include <stdio.h>
#include <stdlib.h>

int A = 25;
int B = 17;
int C;

int main() {
	C = A + B;
	printf("%d + %d is %d", A, B, C);
	return 0;
}
```

- compile with `gcc`
- execute `a.out`
- `objdump` returns assembly from machine code


```C
//stored as 32-bit 0000 0000 0000 1111
int x = 15;
int x = 0xF;
```

---

>[!warning]

`>>`, `<<` SHIFTING

- unsigned = logical
- signed = arithmetic

- default int, etc. are **signed.**

---
