# 2) Dado a sequência de Fibonacci, onde se inicia por 0 e 1 e o próximo valor sempre será a soma dos 2 valores anteriores (exemplo: 0, 1, 1, 2, 3, 5, 8, 13, 21, 34...), escreva um programa na linguagem que desejar onde, informado um número, ele calcule a sequência de Fibonacci e retorne uma mensagem avisando se o número informado pertence ou não a sequência.
```
#include <stdio.h>
#include <stdlib.h>

// Definição da estrutura de dados para um nó
typedef struct Node {
    int value;
    struct Node *next;
} Node;

// Cria um novo nó com um valor específico
Node* create(int value) {
    Node* new_node = (Node*)malloc(sizeof(Node));
    if (!new_node) return NULL;
    new_node->value = value;
    new_node->next = NULL;
    return new_node;
}

// Libera a memória alocada
void release(Node* first) {
    Node* aux;
    while (first != NULL) {
        aux = first;
        first = first->next;
        free(aux);
    }
}

// Verifica se está na sequência de Fibonacci
int verifyFibonacci(Node* first, int num) {
    Node* current = first;
    while (current != NULL) {
        if (current->value == num) return 1; // Retorna caso encontre
        current = current->next;
    }
    
    return 0; // Retorna caso não encontre 
}

int imprime() {
    int num, a = 0, b = 1, next = 0;
    printf("Informe um número para verificar na sequência de Fibonacci: ");
    scanf("%d", &num);
    
    Node* first = create(0);
    Node* current = first;
    
    // Caso especial
    if (num == 0) {
        printf("O número 0 pertence à sequência de Fibonacci.\n");
    }
    else {
        // Calcula a sequência de Fibonacci e armazena na lista encadeada.
        while (next <= num) {
            next = a + b; 
            a = b; 
            b = next; 
            current->next = create(next); 
            current = current->next; 
        }
        // Verifica se o número informado está na sequência.
        if (verifyFibonacci(first, num)) {
            printf("O número %d pertence à sequência de Fibonacci.\n", num);
        } else {
            printf("O número %d não pertence à sequência de Fibonacci.\n", num);
        }
    }
    
    // Libera a memória alocada para a lista encadeada.
    release(first);
    return 0; // Encerra o programa.
}

int main() {
    imprime();
}
```
