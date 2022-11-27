# string and constant charaters

### Summary

The bast way to declare string is the "**character array**"\
char is\_a\_string\[] = "abc";\
char is\_a\_string\[10] = "abc";\
\
This is a **constant** char array.\
char\* is\_a\_const = "abc"

### True or False

```
#include <stdio.h>
#include <string.h>


int main() {

    //A) F
    //The string "char* pc1" is a read-only literal (formally its type is const char[4]).
    // -->char pc1[5] = "john";
    // It's a CONST !!! You can't use char* to change constant.
    char* pc1 = "john";
    *pc1 = 'J';

    //B) T
    char pc2[] = "john";
    *pc2 = 'J';

    //C) F
    //may use "restrict"
    //"Hello, " is a "const char[]"，but a "char array"
    // It's a CONST !!! You can't use char* to change constant.
    char* str1 = "Hello, ";
    char* str2 = "world! ";
    strcat(str1, str2);

    //D) F
    // char* pc3; --> error: ‘pc3’ is used uninitialized in this function
    // Even if initialized pc3, It's a CONST, too !!!
    // You can't use char* to change constant.
    char* pc3;
    *pc3 = 'a';

    return 0;
}
```
