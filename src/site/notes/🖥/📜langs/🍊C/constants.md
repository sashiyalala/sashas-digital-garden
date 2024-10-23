---
{"dg-publish":true,"permalink":"/🖥/📜langs/🍊C/constants/","tags":["c","programming"]}
---


there are many ways to define constants in C

# define
>[!definition] the `#define` *preprocessor* directive

```c
#define <VAR_NAME> <VALUE>
```

>[!warning] NOT REAL constants!!
>⚠ they can be redefined later (but might raise warnings during compilation)
## e.g.
```c
#include <stdio.h>

#define CONSTANT_1 VALUE_1
#define CONSTANT_2 VALUE_2

int main()
    {
        //statements here
    }
```

>[!tip] observe how the `includes` are before the `defines`!
# const
>[!definition] the `const` qualifier

```c
const <data-type> <var_name> = <value>; 
```

>[!warning] cannot be redefined
>once you've assigned a value to a `const` variable, the compiler will throw an error if you try to reassign a value to the constant
## e.g.
```c
#include <stdio.h>

int main()
{
    const int STUDENT_ID = 27;
    const int COURSE_CODE = 502;
    printf("Student ID: %d is taking the class %d\n", STUDENT_ID, COURSE_CODE);

    return 0;
}
```



