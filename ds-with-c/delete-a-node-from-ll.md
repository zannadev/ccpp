# Delete a Node from LL

### Explanation

```
* Step 0: ListNode* prev = NULL;
*         ListNode* node = *head;

*      now head
*        v v
* NULL   "0" -> "1" -> "2" -> "3" -> "4" -> NULL
* ^prev
*
*
* Step 1: while to find the target: "2";
* 
*      head           now
*        v             v
*       "0" -> "1" -> "2" -> "3" -> "4" -> NULL
*               ^prev
*
*
* Step 2: prev->next = now->next;
* 
*      head           now
*        v             v
*       "0" -> "1" -> "2" -> "3" -> "4" -> NULL
*               ^prev-------> ^next
*
*
* Step 3: free(now)
* 
*      head           
*        v             
*       "0" -> "1" ->    -> "3" -> "4" -> NULL
*                            ^prev
```

### C version

```
#include <stdio.h>
#include <stdlib.h>

struct Node {
    struct Node* next;
    int val;
};


void traverse(struct Node** head){
    struct Node* curr = *head;

    while(curr != NULL){
        printf("Value: %d\n", curr->val);
        curr = curr->next;
    }
}


void addNodeToLL(struct Node** head, int val){
    struct Node* new = (struct Node*) malloc(sizeof(struct Node));
    new->val = val;
    new->next = *head;
    *head = new;
}

void deleteNodeToLL(struct Node** head, int val){

    struct Node* now = *head;
    struct Node* prev = NULL;

    if(now != NULL && now->val == val){
        *head = now->next;
        free(now);
    }

    while(now != NULL && now->val != val){
        prev = now;
        now = now->next;
    }

    if(now == NULL){
        // no any node can be delete
        return;
    }

    // start to delete
    prev->next = now->next;
    free(now);
}

```

#### Test code

```
int main() {
   
    struct Node* root = NULL;

    addNodeToLL(&root, 0);
    addNodeToLL(&root, 1);
    addNodeToLL(&root, 2);
    addNodeToLL(&root, 3);
    addNodeToLL(&root, 4);
    
    traverse(&root);

    deleteNodeToLL(&root, 2);
    traverse(&root);
    return 0;
}
```
