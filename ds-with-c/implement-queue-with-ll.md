# Implement Queue with LL

### Explanation

```
* // Definition:
* 
*           back          front
*            v             v
*    Q:     "1" <- "2" <- "3" 
*
*
* // enQueue: Push an element from the "back"
* 
*           back          front
*            v             v
*    Q:     "1" <- "2" <- "3" 
*
*  Step 1: create a Node: new = "0"
*
*  Step 2: add from the back, therefore, 
*          new->next = back
*
*           back          front
*            v             v
*    "0" -> "1" <- "2" <- "3"
*
*  Step 3: back->next = new
*
*     |---- back          front
*     v      v             v
*    "0"    "1" <- "2" <- "3"
*
*  Step 4: back = new
*
*    back                 front
*     v                    v
*    "0" <- "1" <- "2" <- "3"
*
*
* // deQueue: Delete an element from the "front"
* 
*           back          front
*            v             v
*    Q:     "1" <- "2" <- "3"
*
*  Step 1: create a Node: tmp to point "front"
*
*                         front
*           back          tmp
*            v             v
*    Q:     "1" <- "2" <- "3"
*
*
*  Step 2: q->front = q->front->next
*
*
*           back   front  tmp
*            v      v      v 
*           "1" <- "2" <- "3"
*
*  Step 3: free(tmp)
*
*           back   front
*            v      v     
*           "1" -> "2"
*
```

### C version

#### Declaration data structures:

```
#include <stdio.h>
#include <stdlib.h>

struct Node{
    struct Node* next;
    int val;
};


struct Queue{
    struct Node* front;
    struct Node* back;
};
```

#### Create Queue and New an element

```
struct Node* newNode(int value){
    struct Node* new_node = (struct Node*) malloc (sizeof(struct Node));
    new_node->val = value;
    new_node->next = NULL;
    return new_node;
}


struct Queue* creatQueue(){
    struct Queue* q = (struct Queue*) malloc (sizeof(struct Queue));
    q->front = NULL;
    q->back = NULL;
    return q;
}
```

#### Enqueue and Dequeue

```
void deQueue(struct Queue *q){
    if(q->front == NULL){
        return;
    }
    struct Node* temp = q->front;

    q->front = q->front->next;

    if (q->front == NULL)
        q->back = NULL;
 
    free(temp);

}


void enQueue(struct Queue *q, int value){
    struct Node* new_node = newNode(value);

    if(q->back == NULL){

        q->front = new_node;
        q->back = new_node;
        return;
    }

    q->back->next = new_node;
    q->back = new_node;
}
```

#### Test code:

```
int main() {
   
    struct Queue* q = creatQueue();
    enQueue(q, 10);
    enQueue(q, 20);
    deQueue(q);
    deQueue(q);
    enQueue(q, 30);
    enQueue(q, 40);
    enQueue(q, 50);
    deQueue(q);
    printf("Queue Front : %d \n", q->front->val);
    printf("Queue back : %d", q->back->val);

    return 0;
}
```
