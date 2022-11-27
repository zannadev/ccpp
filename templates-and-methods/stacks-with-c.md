---
description: Basic template and methods
---

# Stacks with C

### Operations:

int pop: return the value of the top node and remove it\
void push: add a new node as top node\
int peek: return the value of the top node\
void printStack

### Construct Stack by Array:

```
#include <stdio.h>
#include <stdlib.h>
#include <stdbool.h>
#include <limits.h>


struct Stack {
    unsigned capacity;
    int top;
    int* array;
};

struct Stack* createStack(unsigned capacity){
    struct Stack* stack = (struct Stack*) malloc(sizeof(struct Stack));
    stack -> capacity = capacity;
    stack -> top = -1;
    stack -> array = (int*)malloc(stack -> capacity * (sizeof(int)));
    
    return stack;
}


bool isFull(struct Stack* stack){
    return stack -> top == stack -> capacity - 1;
}

bool isEmpty(struct Stack* stack){
    return stack -> top == - 1;
}


int pop(struct Stack* stack){
    if(isEmpty(stack)){
        return INT_MIN;
    }
    return stack->array[stack->top--];
}


void push(struct Stack* stack, int data){
    if(isFull(stack)){
        return;
    }
    stack->array[++stack->top] = data;
}

int peak(struct Stack* stack){
    if(isEmpty(stack)){
        return INT_MIN;
    }
    return stack->array[stack->top];
}

void printStack(struct Stack* stack){
    if(isEmpty(stack)){
        return;
    }
    
    for(int i = 0; i < stack->capacity; i++){
        printf("stack[%d] = %d \n", i, stack->array[i]);
    }
}

```

### Test Code:

```
int main(){

    struct Stack* stack = createStack(4);
 
    push(stack, 10);
    push(stack, 20);
    push(stack, 30);
 
    printf("%d popped from stack\n", pop(stack));
    
    printStack(stack);

    return 0;
}
```

### Construct Stack by Linked List:

```
#include <stdio.h>
#include <stdlib.h>
#include <stdbool.h>
#include <limits.h>

struct stackNode {
    int data;
    struct stackNode* next;
};

struct stackNode* newNode(int data){
    struct stackNode* node = (struct stackNode*) malloc(sizeof(struct stackNode));
    node -> data = data;
    node -> next = NULL;

    return node;
}


bool isEmpty(struct stackNode* top){
    return !top;
}


int pop(struct stackNode** top){
    if(isEmpty(*top)){
        return INT_MIN;
    }
    
    struct stackNode* tmpNode = *top;
    *top = (*top)->next;

    int popped = tmpNode->data;
    free(tmpNode);
    
    return popped;
}


void push(struct stackNode** top, int data){

    struct stackNode* node = newNode(data);
    
    node->next = *top;
    *top = node;
}

int peek(struct stackNode* top){
    if(isEmpty(top)){
        return INT_MIN;
    }
    return top->data;
}

void printStack(struct stackNode** top){
    if(isEmpty(*top)){
        return;
    }
    
    int i = 0;
    while( *top != NULL){
        printf("top[%d] = %d \n", i, (*top)->data);
        *top = (*top)->next;
    }
}
```

### Test Code:

```
int main(){

    struct stackNode* root = NULL;
 
    push(&root, 10);
    push(&root, 20);
    push(&root, 30);
 
    printf("%d popped from stack\n", pop(&root));
 
    printf("Top element is %d\n", peek(root));
 
 
    printStack(&root);

    return 0;
}
```

[https://www.geeksforgeeks.org/stack-data-structure-introduction-program/](https://www.geeksforgeeks.org/stack-data-structure-introduction-program/)
