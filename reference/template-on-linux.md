# Template on Linux

### Version 1.

\
Makefile

```
main: main.o
<TAB>gcc main.o -o main

main.o: main.c
<TAB>gcc main.c -Wall -Werror -c

clean:
<TAB>rm -rf *.o
```

main.c

```
#include <stdio.h>

int my_func(const char* s1, const char* s2){
    //code
}


int main() {
    //code
    return 0;
}
```

### Version 2.

```
char* URLify(char* testStr, int len){
    
    ...
    return testStr;
}


int main(int argc, char *argv[]) {

    // check the number of argc
    if (argc != 2 ) {
        printf("Correct Syntax: ./urlify \"string\" ");
        exit(1);
    }

    //argv[0] == ./urlify
    //argv[1] == "string"
    int length = strlen(argv[1]);
    char *sentence = (char *) malloc( sizeof(char) * (length * 3 + 1) );
    sentence = argv[1];
  
    printf("Input: %s\n", sentence);
    printf("Output: %s\n", URLify(sentence, length));

    return 0;
}
```
