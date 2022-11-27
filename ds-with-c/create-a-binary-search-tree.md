# Create a Binary search tree

### Properties:

1. leaf -> left < leaf && leaf < leaf->right
2. if traverse as inorder,\
   the sequence will be increasing.

### Code:

```
#include <stdio.h>
#include <stdlib.h>

struct Node {
    struct Node* left;
    struct Node* right;
    int val;
};


struct Node* newNode(int val){
    struct Node* new = (struct Node*)malloc(sizeof(struct Node));

    new->val = val;
    new->left = NULL;
    new->right = NULL;
    return new;
}


struct Node* insertBST(struct Node* head, int val){
    if(head == NULL){
        return newNode(val);
    }

    if(val < head->val){
        head->left = insertBST(head->left, val);
    }else if (val > head->val) {
        head->right = insertBST(head->right, val);
    }

    return head;
}


void inorder(struct Node* head){

    if(head != NULL){
        inorder(head->left);
        printf("Node: %d\n", head->val);
        inorder(head->right);
    }
}
```

#### Test code:

```
int main() {
   
    struct Node* root = NULL;

    root = insertBST(root, 7853);
    insertBST(root, 30);
    insertBST(root, 999);
    insertBST(root, 40);
    insertBST(root, -9);
    insertBST(root, 70);
    insertBST(root, -999);
    insertBST(root, 80);

    inorder(root);

    return 0;
}
```

#### Reference:

[https://www.geeksforgeeks.org/binary-search-tree-set-1-search-and-insertion/](https://www.geeksforgeeks.org/binary-search-tree-set-1-search-and-insertion/)
