# Maximum Subarray

Given an integer array nums, find the contiguous subarray (containing at least one number) which has the largest sum and return its sum.\
[https://leetcode.com/problems/maximum-subarray/](https://leetcode.com/problems/maximum-subarray/)

### Explanation:

![](<../.gitbook/assets/Maximum Subarray.png>)

### Algorithm:

```
#include <stdio.h>

int maximumSubarray(int* array, int len){
    int tmpMax = array[0];
    
    int finalMax = tmpMax;
    for(int i = 1; i < len; i++){
        if(tmpMax + array[i] < array[i]){
            tmpMax = array[i];
        }else{
            tmpMax += array[i];
        }

        if(tmpMax > finalMax){
            finalMax = tmpMax;
        }
    }
    return finalMax;
}
```

### Test:

```
int main(){
    int array[] = {1, 2, 3, 4, 5, -10, 20, 30, -40, 10};
    int len = sizeof(array) / sizeof(array[0]);

    printf("Result of Maximum Subarray is : %d \n", maximumSubarray(array, len));
    
    return 0;
}
```
