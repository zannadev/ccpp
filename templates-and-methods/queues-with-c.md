---
description: Basic template and methods
---

# Queues with C

### Operations:

int peek − Gets the element at the front of the queue without removing it.\
bool isFull − Checks if the queue is full.\
bool isEmpty − Checks if the queue is empty.\
void enQueue − add (store) an item to the queue.\
void deQueue − remove (access) an item from the queue.\
void printQueue

### Construct Queue by Array:

```
#include <stdio.h>
#include <stdlib.h>
#include <stdbool.h>
#include <limits.h>


struct Queue {
    unsigned capacity;
    int size;
    int front; // index of the front node
    int rear; // index of the last one
    int* array;
};

struct Queue* createQueue(unsigned capacity){
    struct Queue* queue = (struct Queue*) malloc(sizeof(struct Queue));
    queue -> capacity = capacity;
    queue -> size = 0;
    queue -> front = 0;
    queue -> rear = capacity - 1; // key !!
    queue -> array = (int*)malloc(queue -> capacity * (sizeof(int)));
    
    return queue;
}


bool isFull(struct Queue* queue){
    return queue -> size == queue -> capacity;
}

bool isEmpty(struct Queue* queue){
    return queue -> size == 0;
}


void enQueue(struct Queue* queue, int data){
    if(isFull(queue)){
        return;
    }
    
    queue->rear = (queue->rear + 1) % queue->capacity;
    queue->size = queue->size + 1;
    queue->array[queue->rear] = data;
}

int deQueue(struct Queue* queue){
    if(isEmpty(queue)){
        return INT_MIN;
    }
    
    int frontData = queue->array[queue->front];
    queue->front = (queue->front + 1 ) % queue->capacity;
    queue->size = queue->size - 1;
    return frontData;
}

int front(struct Queue* queue){
    if(isEmpty(queue)){
        return INT_MIN;
    }
    return queue->array[queue->front];
}

int rear(struct Queue* queue){
    if(isFull(queue)){
        return INT_MIN;
    }
    return queue->array[queue->rear];
}
    

void printQueue(struct Queue* queue){
    if(isEmpty(queue)){
        return;
    }
    
    for(int i = queue->front; i < queue->rear + 1; i++){
        printf("queue[%d] = %d \n", i, queue->array[i]);
    }
}

```

### Test Code:

```
int main(){

    struct Queue* queue = createQueue(10);
 
    enQueue(queue, 10);
    enQueue(queue, 20);
    enQueue(queue, 30);
    enQueue(queue, 40);
 
    printf("%d dequeued from queue\n\n",
           deQueue(queue));
 
    printf("Front item is %d\n", front(queue));
    printf("Rear item is %d\n", rear(queue));
    printQueue(queue);

    return 0;
}
```

### Construct Queue by Linked List:

```
#include <stdio.h>
#include <stdlib.h>
#include <stdbool.h>
#include <limits.h>

struct queueNode {
    int data;
    struct queueNode* next;
};

struct Queue {
    struct queueNode *front, *rear;
    unsigned capacity;
    int size;
};

struct queueNode* newNode(int data){
    struct queueNode* node = (struct queueNode*) malloc(sizeof(struct queueNode));
    node -> data = data;
    node -> next = NULL;

    return node;
}

struct Queue* createQueue(unsigned capacity){
    struct Queue* queue = (struct Queue*) malloc (sizeof (struct Queue));
    
    queue->capacity = capacity;
    queue->size = 0;
    queue->front = NULL;
    queue->rear = NULL;
    
    return queue;
    
}


bool isFull(struct Queue* queue){
    return queue -> size == queue -> capacity;
}

bool isEmpty(struct Queue* queue){
    return queue -> size == 0;
}


void enQueue(struct Queue* queue, int data){

    if(isFull(queue)){
        return;
    }
    
    struct queueNode* node = newNode(data);
    
    if(isEmpty(queue)){
        queue->front = node;
        queue->rear = node;
        queue->size = 1;
        return;
    }
    
    queue->rear->next = node;
    queue->rear = node;
    queue->size = queue->size + 1;
}

int deQueue(struct Queue* queue){
    if(isEmpty(queue)){
        return INT_MIN;
    }
    
    struct queueNode* tmp = queue->front;
    
    int frontData = tmp->data;
    queue->front = queue->front->next;
    
    if(queue->front == NULL){
        queue->rear = NULL;
    }
    queue->size = queue->size - 1;
    free(tmp);
    
    return frontData;
}

int front(struct Queue* queue){
    if(isEmpty(queue)){
        return INT_MIN;
    }
    return queue->front->data;
}

int rear(struct Queue* queue){
    if(isFull(queue)){
        return INT_MIN;
    }
    return queue->rear->data;
}
    

void printQueue(struct Queue* queue){
    if(isEmpty(queue)){
        return;
    }

    int i = 0;
    struct queueNode* q = queue->front;
    while( q != NULL){
        printf("Node[%d] = %d \n", i, q->data);
        q = q->next;
    }
}
```

### Test Code:

```
int main(){

    struct Queue* queue = createQueue(10);
 
    enQueue(queue, 10);
    enQueue(queue, 20);
    deQueue(queue);
    deQueue(queue);
    enQueue(queue, 30);
    enQueue(queue, 40);
    enQueue(queue, 50);
    deQueue(queue);
 

    printf("Front item is %d\n", front(queue));
    printf("Rear item is %d\n", rear(queue));
    printQueue(queue);

    return 0;
}
```

[https://www.geeksforgeeks.org/queue-set-1introduction-and-array-implementation/](https://www.geeksforgeeks.org/queue-set-1introduction-and-array-implementation/)\
[https://www.geeksforgeeks.org/queue-linked-list-implementation/](https://www.geeksforgeeks.org/queue-linked-list-implementation/)
