---
{"dg-publish":true,"permalink":"/🖥/📜langs/🍊C/the static keyword/","tags":["c","cpp","programming"]}
---


can have different meanings (🔗[source](https://stackoverflow.com/q/572547/12575557))

# static variable in a scope
>[!definition] static variable
> a static variable inside a function keeps its value between invocations. 

a declared variable in a fn, or more generally in a scope (a pair of `{}`), is liberated by the OS once the fn/scope finishes.
static variables, once declared, are not liberated though

E.g. 
```c
#include <stdio.h>

void foo()
{
    int a = 10;
    static int sa = 10;
    
    a += 5;
    sa += 5;
    
    printf("a = %d, sa = %d\n", a, sa);
}


int main()
{
    int i;
    
    for (i = 0; i < 10; ++i)
        foo();
}

```

this code ⬆ prints:
>[!note] `a` normal & `sa` static ✔
```c
a = 15, sa = 15
a = 15, sa = 20
a = 15, sa = 25
a = 15, sa = 30
a = 15, sa = 35
a = 15, sa = 40
a = 15, sa = 45
a = 15, sa = 50
a = 15, sa = 55
a = 15, sa = 60
```
# static in file declarations
a global variable or fn declared as static means they're only "seen" in the file where they're declared
>[!info] pro of declaring static global vars/fns
> - [p] visual hint that the global var/fn is only used in that file
> - [p] during linking there is no clashing between global vars/fns that have the same name 
> 	- [!] you use anon namespaces in C++ for this
> - [p] no `static`  declared things can be accessed from outside the file
## static global variable
## static function

and specific usages by language:
# C
## static in array declarations
to specify minimum size of the array in fn declarations
>[!warning] non-fn array declarators cannot use this keyword

```c
void func(int foo[static 42]);
```
>[!info] the `func` fn takes an array of *at least* 42 elements
# C++
## static class attributes
methods that are shared between all objects of the same class.
they don't depend on the instance