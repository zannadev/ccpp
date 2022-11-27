# Reverse Linked List

### Explanation

```
* Step 0: ListNode* prev = NULL;
*         ListNode* next = NULL;
*         ListNode* curr = head;
* 
*           curr head
*              v v
*    NULL      "1" -> "2" -> "3" -> NULL
* prev^ ^next
*
*
* Step 1: next = curr->next;
* 
*           curr head
*              v v
*    NULL      "1" -> "2" -> "3" -> NULL
* prev^                ^next
*
*
* Step 2: curr->next = prev;
* 
*           curr head
*              v v
*    NULL  <-- "1"    "2" -> "3" -> NULL
* prev^                ^next
*
*
* Step 3: prev = curr;
*         curr = next;
* 
*                head  curr
*                v     v
*    NULL  <-- "1"    "2" -> "3" -> NULL
*           prev^      ^next
```

### C version

```
#include <stdio.h>
#include <stdlib.h>

struct Node{
    struct Node* next;
    int val;
};


void reverse(struct Node **head){
    struct Node* prev = NULL;
    struct Node* next = NULL;
    struct Node* now = *head;

     
    while(now != NULL){
        next = now->next;
        now->next = prev;
        prev = now;
        now = next;
    }
    *head = prev;
}


void enqueue(struct Node **root, int value){
    struct Node* new_node = (struct Node*) malloc (sizeof(struct Node));
    new_node->val = value;
    new_node->next = *root;
    *root = new_node;

}

void traverse(struct Node* ref){
    struct Node* tmp = ref;
    while(tmp!= NULL){
        printf("%d\n", tmp->val);
        tmp = tmp->next;
    }
}
```

Test code:

```
int main() {
   
    struct Node* root = NULL;

    enqueue(&root, 0);
    enqueue(&root, 1);
    enqueue(&root, 2);
    enqueue(&root, 3);
    enqueue(&root, 4);
    
    traverse(root);
    reverse(&root);
    traverse(root);
    return 0;

}
```

### Version 2: with single pointer head

```
void reverse(struct Node *head){
    struct Node* prev = NULL;
    struct Node* next = NULL;
    struct Node* now = head;

     
    while(now != NULL){
        next = now->next;
        now->next = prev;
        prev = now;
        now = next;
    }
    head = prev;
}
```
