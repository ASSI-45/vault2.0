-- -

1. include `<stdio.h>`
2. Make pointer to file using the `FILE` datatype, this is equal to `fopen(file, "r"`
3. write a for loop with `fgetc(pF) != EOF`
4. close with `fclose`
```c 
#include <stdio.h>

void open_file(char *file) {
    FILE *pF = fopen(file, "r");

    char ch;
    while ((ch = fgetc(pF)) != EOF) {
        printf("%c", ch);
    }

    fclose(pF);

}
```