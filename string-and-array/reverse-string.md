# Reverse string

### Explanation

### C version

```
#include <stdio.h>

void reverse (char* string){

    char *end = string;
    while(*end != '\0'){
        end++;
    }
    end--;
    
    
    char* begin = string;
    char tmp;
    while(begin < end) {
        tmp = *begin;
        *begin = *end;
        *end = tmp;

        begin++;
        end--;
    }
}
```

#### Test

```
int main() {
   
    char test[100] = "abcdefg";
    printf("sting: %s\n", test);
    reverse(test);
    printf("reverse: %s\n", test);
    return 0;

}
```
