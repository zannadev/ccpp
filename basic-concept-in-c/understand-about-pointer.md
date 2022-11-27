# Understand about pointer

### Common

**int\*** ptr is a declaire of value,\
this value save "address"\
\
int b = 0\
**ptr** = \&b\
\
ptr saved the address of b\
\*ptr is deregister of \&b\
therefore, **\*ptr** == 0, it's a integer.

### Question 1.

```
#include <stdio.h>

int main(){
    
    char* name[] = {"abcde", "fghijklm", "nopq"};
    printf("%c\n", *(*(name+1)+2));
    printf("%c\n", name[1][2]);

    return 0;
}
```

