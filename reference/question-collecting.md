# Question Collecting:

1.\
CICT\
Ch 02 - Linked List

2.\
Ch 05 - Bit Manipulation

```
01 - Insertion
02 - Binary to String
03 - Flip Bit to Win
04 - Next Number
05 - Debugger
06 - Conversion
07 - Pairwise Swap
08 - Draw Line
```

3.\
Please explain the difference between the following two functions in standard C library. Explain the meaning of the qualifiers const and restrict. What can happen if the object pointed to by s1 and the object pointed to by s2 overlap?

\#include \<string.h>\
void \*_memcpy(void_ restrict si, const void\* restrict s2, size\_t n);\
void \*memmove(void \*s1, const void \*s2, size\_t n);\


4.\
add two matrix within O(N^2)\


6.\
What problem will the code cause? (Hint: Multi-threading issues.)

```
static int count =1;

void* incr_count(void*p) {
    ++count;
    return 0;
}

static pthread_mutex_t m1 = PTHREAD_MUTEX_INITIALIZER;
static pthread_mutex_t m2 = PTHREAD_MUTEX_INITIALIZER;

void* lock_m1_then_m2(void*p){
    pthread_mutex_lock(&m1);
    pthread_mutex_lock(&m2);
    pthread_mutex_unlock(&m2);
    pthread_mutex_unlock(&m1);
    return 0;
}

void* lock_m2_then_m1(void*p){
    pthread_mutex_lock(&m2);
    pthread_mutex_lock(&m1);
    pthread_mutex_unlock(&m1);
    pthread_mutex_unlock(&m2);
    return 0;
}

int main(void){
    pthread_t ti, t2, t3, t4;
    pthread_create(&t1, NULL, incr_count, NULL);
    pthread_create(&t2, NULL, incr_count, NULL);
    pthread_create(&t3, NULL, lock_m1_then_m2, NULL);
    pthread_create(&t4, NULL, lock_m2_then_m1, NULL);
    pthread_join(t4, NULL);
    pthread_join(t3, NULL);
    pthread_join(t2, NULL);
    pthread_join(t1,NULL);
    return count;
}
```

7.\
Why does the program not exit ?

```
#include <stdio.h>
#include <unistd.h>
#include <pthread.h>

pthread mutex_t mutex1;
pthread_mutext mutex2;
static int count = 0;

void func1(void arg){
    while((*(int*)(arg))<200){
        pthread_mutex_lock(&mutex1);
        pthread mutex_lock(&mutex2);
        *(int*)arg = *(int*)(arg) + 1;

        printf("thread a\n", *(int*)arg);
        pthread_mutex_unlock(&mutex2);
        pthread_mutex_unlock(&mutex1);

    }
}


void* func2(void* arg){
    while((*(int*)(arg))<200){
        pthread_nutex_lock(&mutex2);
        pthread mutex_lock(&mutex1);
        *(int*)arg = *(int*)(arg) + 1;
        printf("thread %d\n", *(int*)arg);
        pthread_mutex_unlock(&mutex1);
        pthread_mutex_unlock(&mutex2);
    }
}

int main(int argc, char argv[]){
    pthread_mutex_init(&mutex1, NULL);
    pthread mutex_init(&mutex2, NULL);

    pthread_t tid1;
    pthread_t tid2;

    pthread_create(&tid1, NULL, func1, (void*) (&count));
    pthread_create(&tid2, NULL, func2, (void") (&count));

    while(1){
        if(count>=200){
            break;
        }else{
            sleep(1);
        }
    }
    return 0;
}
```



9\. What's the difference between heap and stack ?

10\. how does violate be implemented ?

11\. Common sense of compiler and OS\
For me, the params of makefile is a little bit important.

12\. sorting, binary tree

13\. How can we avoid the issue of synchronize problem ? mutex ?\
[https://stackoverflow.com/questions/5515276/synchronization-problems-in-c-using-pthreads-mutexes](https://stackoverflow.com/questions/5515276/synchronization-problems-in-c-using-pthreads-mutexes)

14\. 判斷 big endian and little endian

OS: interrupt

OS: 怎麼 sync 多個 threads
