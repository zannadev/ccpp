# Pre/Post Increment Operator

## Q1:

```
int arr[] = {10, 20, 30, 40, 50, 60};
int* ptr = arr;
*(ptr++) += -1; // 9, 20, 30, 40, 50, 60
*(++ptr) += -2; // 9, 20, 28, 40, 50, 60
ptr += 2;
*ptr += -3;// 9, 20, 28, 40, 47, 60
```

#### Ans:

9, 20, 28, 40, 47, 60

#### Demo:

```
#include <stdio.h>

int main(){
    int arr[] = {10, 20, 30, 40, 50, 60};
    int* ptr = arr;
    *(ptr++) += -1; // 9, 20, 30, 40, 50, 60
    *(++ptr) += -2; // 20, 20, 28, 40, 50, 60
    ptr += 2;
    *ptr += -3;// 20, 20, 40, 40, 47, 60
    
    for(int i = 0; i < sizeof(arr) / sizeof(arr[0]); i++){
        printf("arr[%d] = %d \n", i, arr[i]);
    }

    return 0;
}

```

### Explanation:

#### int\* ptr = arr;

```
     ptr V  
arr[] = {10, 20, 30, 40, 50, 60};
```

#### \*(ptr++) += -1;

_++在 ptr 後面, 他會先賦值再移動指標_\
Step 1.  \*ptr --> 10\
Step 2. \*ptr = \*ptr + (-1) --> arr\[0] = 9\
Step 3.  ptr++ --> this pointer has shifted to arr\[1]&#x20;

#### \*(++ptr) += -2;

_++在 ptr 前面, 他會先移動再賦值_\
Step 1. ++ptr --> this pointer has shifted to arr\[2]\
Step 2. \*(++ptr) == arr\[2] = 30\
Step 3. \*(++ptr) = \*(++ptr) + (-2) -->  arr\[2] = arr\[2] -2\
&#x20;                                                        \--> arr\[2] = 28

#### ptr += 2

ptr += 2 --> this pointer has shifted to arr\[4]

#### \*ptr += -3

\*ptr += -3 --> arr\[4] = arr\[4] -3\
&#x20;                 \--> arr\[4] = 47

### Summary:

```
(1)
a = ptr++
ptr的值先給 a, ptr再加 1

a = ++ptr
ptr先加 1, ptr的值再傳給 a


(2)
*(ptr++)
++在 ptr 後面, 他會先賦值再移動指標

*(++ptr)
++在 ptr 前面, 他會先移動再賦值
```
