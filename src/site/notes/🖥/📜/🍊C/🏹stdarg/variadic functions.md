---
{"dg-publish":true,"permalink":"/🖥/📜/🍊C/🏹stdarg/variadic functions/","tags":["c"]}
---



>[!definition] variadic function
>a function whose total number of arguments is unknown at the beginning
>

>[!example] e.g., [[🖥/📜/🍊C/🖨stdio/🖨 printf\|🖨 printf]]

![1_zgeqS3hG7hR6c0zHYene2Q.webp](/img/user/1_zgeqS3hG7hR6c0zHYene2Q.webp)

# va things

`va_list`, `va_start`... are all **macros** from the `stdarg` include.

>[!warning] 42
>`va_list` (unused in 42 [[☆⋆｡𖦹°‧★🛸42/⋆｡ﾟ🪐｡⋆ ﾟ☾ ﾟ⋆common-core/01/🖨ft_printf/🖨ft_printf\|🖨ft_printf]])

| macro               | description: a macro that...                                                                       |
| ------------------- | -------------------------------------------------------------------------------------------------- |
| `va_list`🚫🚫🚫🚫🚫 | ...is a type to declare a variable that will hold the **variable argument list**                   |
| `va_start`          | ...initializes a `va_list` variable to point to the 1st argument in the **variable argument list** |
| `va_arg`            | ...retrieves the *next* argument in the **variable argument list** with a specified type           |
| `va_copy`           | ...copies a `va_list` variable to another one                                                      |
| `va_end`            | ...cleans up the `va_list` variable after it has been used                                         |

```c
va_start, va_arg, va_copy, va_end
```