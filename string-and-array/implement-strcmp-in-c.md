# implement strcmp in C

### Better version

```
#include <stdio.h>

int z_strcmp (char* str1, char* str2){

    printf("str1: %s, str2: %s\n", str1, str2);
    while( *str1!= '\0' && *str1 - *str2 == 0){
        str1++;
        str2++;
    }
    return *str1 - *str2 != 0 ? -1: 0;
}
```

### Worse version

```
#include <stdio.h>

int _strcmp (char* str1, char* str2){
    char* ptr1 = str1;
    char* ptr2 = str2;

    printf("str1: %s, str2: %s\n", str1, str2);
    while( *ptr1!= '\0' && *ptr2 != '\0'){
        if(*ptr1 != *ptr2){
            return -1;
        }
        ptr1++;
        ptr2++;
    }
    if(*ptr1 - *ptr2 == 0){
        return 0;
    }
    return -1;
}
```

#### Test code

```
int main() {
    printf("result: %d\n", z_strcmp("","accccc"));
    return 0;
}
```
