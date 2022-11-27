# Find mid of LL without traverse

### Explanation

key: use slow and fast pointer\
Pay attention about the even or odd case !

### C version

```
#include <stdio.h>
#include <stdlib.h>


struct Node {
    struct Node* next;
    int val;
};


void addInTail(struct Node **head, int val){
    struct Node* new = (struct Node*) malloc (sizeof(struct Node));
    new->val = val;
    new->next = *head;
    *head = new;
    printf("Node: %d\n", new->val);
}


int findMidOfLL (struct Node** head){
    struct Node* slow = *head;
    struct Node* fast = *head;

    while(fast->next != NULL && fast->next->next != NULL){
        fast = fast->next->next;
        slow = slow->next;
    }

    if(fast->next->next == NULL){ //it's even
        printf("Event\n");
        return ((slow->val + (slow->next)->val)/2);
    }else {
        printf("Odd\n");
        return (slow->next)->val;
    }
}

```

#### Test Code

```
int main() {
    struct Node* head = NULL;
    
    addInTail(&head, 0);
    addInTail(&head, 1);
    addInTail(&head, 3);
    addInTail(&head, 8);
    addInTail(&head, -100);
    addInTail(&head, 49);
    addInTail(&head, 2);
    addInTail(&head, -88);

    printf("Mid: %d\n", findMidOfLL(&head));
    return 0;
}
```
