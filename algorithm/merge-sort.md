# Merge Sort

### Explanation:

picture

### Code:

```
#include <stdio.h>

void mergeSubArrays(int array[], int idxL, int idxM, int idxR){
    int i1, i2, idx;
    int lenL = idxM - idxL + 1;
    int lenR = idxR - idxM;
    
    int L[lenL], R[lenR];
    
    // copy array to arrayL and arrayR
    for(i1 = 0; i1 < lenL; i1++){
        L[i1] = array[idxL + i1];
    }
    for(i2 = 0; i2 < lenR; i2++){
        R[i2] = array[idxM + i2 + 1];
    }
    
    
    i1 = 0;
    i2 = 0;
    idx = idxL;
    while( i1 < lenL && i2 < lenR){
        if(L[i1] < R[i2]){
            array[idx] = L[i1];
            i1++;
        }else{
            array[idx] = R[i2];
            i2++;
        }
        idx++;
    }
    
    // put the lase elements to array
    while(i1 < lenL){
        array[idx] = L[i1];
        idx++;
        i1++;
    }
    while(i2 < lenR){
        array[idx] = R[i2];
        idx++;
        i2++;
    }
}


void mergeSort(int array[], int idxL, int idxR){
    // seperate to sub arrays
    if(idxL < idxR){
        int m = idxL + (idxR - idxL) /2 ;
        mergeSort(array, idxL, m);
        mergeSort(array, m + 1, idxR);
        
        mergeSubArrays(array, idxL, m, idxR);
    }
}

```

#### Test:

```
int main(){
    int array[] = {3, 8, -5, 55, 1};
    int len = sizeof(array) / sizeof(array[0]);
    mergeSort(array, 0, len - 1);
    
    for(int i = 0; i < len; i++){
        printf("array[%d] = %d \n", i, array[i]);
    }
    return 0;
}
```

[https://www.geeksforgeeks.org/merge-sort/](https://www.geeksforgeeks.org/merge-sort/)
