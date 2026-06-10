b 
## static memory allocation
-- -
Static memory is memory that can't shrink or change location.

+ `*` -> is used for making a pointer and referencing a pointer, A pointer is a sort of data type that saved a memory addres. Later on you can also do pointer arithmetic to go through an array for example
+ `&` -> Is used to retrive a memory addres

```c
#include <stdio.h>

int main(void) {
	int x = 5;
	int *i = &x;
	printf("%d", *i);
}
```

## dynamic memory allocation
---
you use this when you don't know how much data is needed to be stored, data type changes data size or is to large for the stack.

```c
#inlude <stdio.h>
#include <stdlib.h>

int main(void) {
	int length

	printf("how long is the array: ",);
	scanf("%d\n", length);
	
	int *arr = (int*)malloc(size * (int)); // allocting dynamic memory
	for (int i = 0; i < length; i++) {
		printf("enter element number %d: ", i);
		scanf("%d", arr + i);
	}

}
```
