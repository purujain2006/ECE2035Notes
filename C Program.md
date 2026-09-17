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

