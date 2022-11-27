# Count Prime

Given an integer `n`, return _the number of prime numbers that are strictly less than_ `n`.[\
https://leetcode.com/problems/count-primes/](https://leetcode.com/problems/count-primes/)

### Algorithm:

```
#include <stdio.h>
#include <math.h>
#include <stdbool.h>

bool isPrime(int n){
    int sq = sqrt(n);
    for(int j = 2; j <= sq; j++){
        if( n % j == 0){
            return false;
        }
    }
    return true;
}

int countPrime(int N){
    int count = 0;
    for(int i = 2; i < N + 1; i++){
        if(isPrime(i)){
            count++;
        }
    }
    return count;
}

```

### Version 2:

```
int countPrime2(int n){
    if( n <= 2 ) return 0;

    int primes[n + 1];
    for (int i = 0; i < n + 1 ; i++){
        primes[i] = 1;
    }
        
    int ret = 0;
    for(int i = 2; i*i <= n; i++){
        if(primes[i] == 1){
            for(int j = i*i; j <= n; j+=i){
                primes[j] = 0;
            }
        }
    }
        
    for(int i = 2; i < n; i++){
        if( primes[i] == 1){
            ret++;
        }
    }
    return ret;
}
```

### Test:

```
int main(){

    int N = 25;
    printf("There are %d prime numbers whthin %d\n", countPrime(N), N);
    return 0;
}
```
