# Bubble Sort

### Explanation:

![](../.gitbook/assets/bubblesort\_1.png)

![](../.gitbook/assets/bubblesort\_2.png)

### Code:

```
#include <stdio.h>

void bubbleSort(int data[], int len){

    for(int i = 1; i < len; i++){
        for(int j = 1; j < len; j++) {
            if(data[j-1] > data[j]){
                int tmp = data[j];
                data[j] = data[j-1];
                data[j-1] = tmp;
            }
        }
    }
}
```

**Make it better:**

```
void bubbleSort(int data[], int len){
    for(int i = 1; i < len; i++){
        for(int j = 1; j < len-i+1; j++) {  <------------------!!!
            if(data[j-1] > data[j]){
                int tmp = data[j];
                data[j] = data[j-1];
                data[j-1] = tmp;
            }
        }
    }
}
```

#### Test code:

```
int main(void){

    int data[] = { -1, 0, 7, -9, 8, -99};

    int len = sizeof(data)/sizeof(data[0]);
    bubbleSort(data, len);

    for (int t = 0; t < len; t++)
        printf("data[%d] = %d \n", t, data[t]);
 
    return 0;
}
```
