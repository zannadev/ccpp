# Insertion Sort

### Explanation:

![](../.gitbook/assets/insertionsort\_1.png)

![](../.gitbook/assets/insertionsort\_2.png)

### Code:

```
#include <stdio.h>

void insertionSort(int data[], int len){

    for(int i = 0; i < len-1; i++){
        for(int j = i + 1; j < len; j++) {
            if(data[i] > data[j]){
                int tmp = data[j];
                for(int k = j; k > i; k--){
                    data[k] = data[k-1];
                }
                data[i] = tmp;
            }
        }
    }
}
```

#### Test code:

```
int main(void){

    int data[] = { -1, 0, 8, -9, 7, -99};

    int len = sizeof(data)/sizeof(data[0]);
    insertionSort(data, len);

    for (int t = 0; t < len; t++)
        printf("data[%d] = %d \n", t, data[t]);
 

    return 0;
}
```
