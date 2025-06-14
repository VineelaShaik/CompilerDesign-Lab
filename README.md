# Ex. No : 1

# IMPLEMENTATION OF SYMBOL TABLE
## Name: Vineela Shaik
## Register Number : 212223040243
# Date :10.03.2025

# AIM:

To write a C program to implement a symbol table.

# ALGORITHM:

1. Start the program.
2. Get the input from the user with the terminating symbol ‘$’.
3. Allocate memory for the variable by dynamic memory allocation function.
4. If the next character of the symbol is an operator then only the memory is allocated.
5. While reading, the input symbol is inserted into symbol table along with its memory address.
6. The steps are repeated till ‘$’ is reached.
7. To reach a variable, enter the variable to be searched and symbol table has been checked for corresponding variable, the variable along with its address is displayed as result.
8. Stop the program.

# PROGRAM:
```
#include <stdio.h>
#include <ctype.h>
#include <string.h>
#include <stdlib.h>
#define MAX_EXPRESSION_SIZE 100
#define MAX_SYMBOLS 15
int main() {
    int i = 0, x = 0, n;
    void *add[MAX_SYMBOLS];
    char b[MAX_EXPRESSION_SIZE], d[MAX_SYMBOLS], c, srch;
    int found = 0;
    printf("Enter the Expression terminated by $: ");
    while ((c = getchar()) != '$' && i < MAX_EXPRESSION_SIZE - 1) {
        b[i++] = c;
    }
    b[i] = '\0';
    n = i - 1;
    printf("Given Expression: %s\n", b);
    printf("\nSymbol Table\n");
    printf("Symbol\taddr\ttype\n");
    for (int j = 0; j <= n && x < MAX_SYMBOLS; j++) {
        c = b[j];
        if (isalpha((unsigned char)c)) {
            if (j == n || strchr("+-*=", b[j+1])) {
                void *p = malloc(sizeof(char));
                add[x] = p;
                d[x] = c;
                printf("%c\t%p\tidentifier\n", c, p);
                x++;
            }
        }
    }
    while (getchar() != '\n'); 
    printf("\nThe symbol to be searched: ");
    srch = getchar();
    for (i = 0; i < x; i++) {
        if (srch == d[i]) {
            printf("Symbol Found\n");
            printf("%c@address%p\n", srch, add[i]);
            found = 1;
            break;
        }
    }
    if (!found) {
        printf("Symbol Not Found\n");
    }
    for (i = 0; i < x; i++) {
        free(add[i]);
    }
    return 0;
}
```
# OUTPUT:
![Screenshot 2025-03-10 110548](https://github.com/user-attachments/assets/8e664f22-ef85-409f-bf62-c7ad7716fe51)


# RESULT:

The program to implement a symbol table is executed and the output is verified.
