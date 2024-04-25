# 5) Escreva um programa que inverta os caracteres de um string.
-  IMPORTANTE:

a) Essa string pode ser informada através de qualquer entrada de sua preferência ou pode ser previamente definida no código;

b) Evite usar funções prontas, como, por exemplo, reverse;
```
#include <stdio.h>
#include <string.h>
#define MAX 100

// Função para inverter a string
void reverseString(char *str) {
    int top = -1;
    char stack[MAX];

    // Empilha todos os caracteres da string
    for (int i = 0; i < strlen(str); i++) {
        stack[++top] = str[i];
    }

    // Desempilha os caracteres e os coloca de volta na string
    for (int i = 0; i < strlen(str); i++) {
        str[i] = stack[top--];
    }
}

int main() {
    char str[MAX];

    printf("Digite uma string: ");
    fgets(str, sizeof(str), stdin);

    reverseString(str);

    printf("String invertida: %s\n", str);

    return 0;
}

```
