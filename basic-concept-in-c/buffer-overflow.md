# buffer​ overflow

### \*\*\* stack smashing detected \*\*\*

A buffer​ overflow occurs when the user input exceeds the buffer capacity. \
https://www.educative.io/edpresso/what-is-the-stack-smashing-detected-error\


### Find the potential exception

```
void* memcpy(void* pvTo, void* pvFrom, size_t size){

    byte* pbTo = (byte*)pvTo;
    byte* pbFrom = (byte*)pvFrom;


    while(size-- > 0)
        *pbTo++ = *pbFrom++;


    return pvTo;
}
```

### Code:

```
#include <stdio.h>
typedef unsigned char byte;

void* z_memcpy(void* restrict pvTo, void* pvFrom, size_t size){
    byte* pbTo = (byte*)pvTo;
    byte* pbFrom = (byte*)pvFrom;


    while(size-- > 0){
        printf("TO: %c, From: %c \n", *pbTo, *pbFrom);
        *pbTo++ = *pbFrom++;
    }
    return pvTo;
}
```

#### Test code

```
int main() {

    char to[4] = "";
    char from[] = "abcdefg";

    z_memcpy(to, from, 14);

    return 0;
}
```
