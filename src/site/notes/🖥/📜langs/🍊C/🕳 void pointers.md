---
{"dg-publish":true,"permalink":"//langs/c/void-pointers/","tags":["c","cheat","programming"]}
---


>[!info] [GNU docs](https://www.gnu.org/software/c-intro-and-ref/manual/html_node/Void-Pointers.html)


>[!definition] void pointers
>a pointer that has no associated data type with it.
>>[!info] it can hold an address of any type and can be **typecasted** to any type

```c
// C Program to demonstrate that a void pointer
// can hold the address of any type-castable type

#include <stdio.h>

int main() {
  int a = 10;
  char b = 'x';

  // void pointer holds address of int 'a'
  void * p = & a;
  // void pointer holds address of char 'b'
  p = & b;
}
```

# properties
## it can't be dereferenced
>[!warning] you can't access the contents of a void pointer "directly"

```c
#include <stdio.h>

int main() {
  int a = 10;
  void * ptr = & a;
  printf("%d", * ptr);

  return 0;
}
```

>[!bug] Compiler Error: 'void*' is not a pointer-to-object type

Per GNU docs, dereferencing a void pointer gives a `void` value that can't be used([The Void Type](https://www.gnu.org/software/c-intro-and-ref/manual/html_node/The-Void-Type.html)) 
## you must type-cast to access its contents
```c
#include <stdio.h>

int main() {
  int a = 10;
  void * ptr = & a;
  // The void pointer 'ptr' is cast to an integer pointer
  // using '(int*)ptr' Then, the value is dereferenced
  // with `*(int*)ptr` to get the value at that memory
  // location
  printf("%d", *(int * ) ptr);
  return 0;
}
```

## passing an argument of type `void*` for typed pointers
You can pass a void pointer as an argument to a function that receives another type of pointer and it will convert automatically
# advantages
- [[🖥/📜langs/🍊C/malloc\|malloc]] & [[🖥/📜langs/🍊C/calloc\|calloc]] return `void *` & this allows them to be used to allocate memory of **any** data type
- they are usually used in C to implement *generic* functions
- when used along with "function pointers" of type `void (*)(void)`, points to the functions that take any arguments and return any value
- mainly used when implementing data structures, e.g. linked lists, trees, queues...i.e., dynamic data structures
- also commonly used for typecasting
