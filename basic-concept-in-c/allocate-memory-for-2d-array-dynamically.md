# Allocate memory for 2D array dynamically

### **Question:**

Please implement it in C - To allocate memory for real 2D array dynamically, be reminded to insert your code based on the comments below accordingly.

```
#include <stdlib.h>

int main(void){

    int **a, m = 500, n = 400, 1, j;
    // Allocate memory for a[m][n] here
    // Insert your code:





    for ( i = 0; i < m; i++){
        for (j = 0; j < n; j++){
            a[i][j] = i+j;
        }
    }
    return 0;
}
```

#### Answer:

```
#include <stdio.h>
#include <stdlib.h>


int main(void){

    int **a, m = 500, n = 400, i, j;
    // Allocate memory for a[m][n] here
    // Insert your code:


    a = (int**) malloc(m * sizeof(int*));
    for(int k = 0; k < m; k++){
        a[k] = (int*) malloc (n * sizeof(int));

    }


    for ( i = 0; i < m; i++){
        for (j = 0; j < n; j++){
            a[i][j] = i+j;
        }
    }

    for ( int k = 0; k < m; k++){
        for (int r = 0; r < n; r++){
            printf("a[%d][%d] = %d \n", k, r, a[k][r]);
        }
    }
    
    for (int t = 0; t < m; t++)
        free(a[t]);
 
    free(a);
    
    return 0;
}

```

[https://www.geeksforgeeks.org/dynamically-allocate-2d-array-c/](https://www.geeksforgeeks.org/dynamically-allocate-2d-array-c/)
