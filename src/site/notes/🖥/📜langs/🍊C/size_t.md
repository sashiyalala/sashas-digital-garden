---
{"dg-publish":true,"permalink":"//langs/c/size-t/","tags":["c","programming"]}
---


>[!info] it's an **unsigned** type


It's arithmetic can't work out negative types, e.g. this doesn't work:

```c
size_t s1 = strlen(str1);
size_t s2 = strlen(str2);
```
