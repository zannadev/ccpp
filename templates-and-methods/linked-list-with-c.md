---
description: Basic template and methods
---

# Linked List with C

### Structure

```
struct Node {
    struct Node* next;
    int val;
};
```

### NewNode

```
struct Node* newNode(int value){
    struct Node* new_node = (struct Node*) malloc (sizeof(struct Node));
    new_node->val = value;
    new_node->next = NULL;
    return new_node;
}
```

### AddToTail

```
void addToTail(struct Node **root, int value){
    struct Node* new_node = (struct Node*) malloc (sizeof(struct Node));
    new_node->val = value;
    new_node->next = *root;
    *root = new_node;
}
```

### Traverse

```
void traverse(struct Node* ref){
    struct Node* tmp = ref;
    while(tmp!= NULL){
        printf("%d\n", tmp->val);
        tmp = tmp->next;
    }
}
```
