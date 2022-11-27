# Short-circuit evaluation

**Question:**

```
boolean A(), boolean B(), boolean C()
Can you find the potential issue ?
if(A() && B())
if(B() && C())
```

**Explanation:**\
In this example, short-circuit evaluation guarantees that myfunc(b) is never called

```
int a = 0;
if (a != 0 && myfunc(b)){
    do_something();
}
```

[https://en.wikipedia.org/wiki/Short-circuit\_evaluation](https://en.wikipedia.org/wiki/Short-circuit\_evaluation)
