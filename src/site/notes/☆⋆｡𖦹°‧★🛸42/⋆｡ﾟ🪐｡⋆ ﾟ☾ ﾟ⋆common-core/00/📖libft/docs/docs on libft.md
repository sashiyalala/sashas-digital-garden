---
{"dg-publish":true,"permalink":"/42/common-core/00/libft/docs/docs-on-libft/","tags":["42madrid","unix","c"]}
---

# libc methods
## `isalpha`
Given an unsigned char, return whether it's an *alphabetic* character
## `isdigit`
Given an unsigned char, return whether it's an *numeric* character
## `isalnum`
Given an unsigned char, return whether it's an alphanumeric character, i.e. `isalnum` <=> (`isalpha || isdigit`)
## `isascii`
Given a number, check whether it's an unsigned char that fits into the ASCII char set.
## `isprint`
Given a number, check whether it's a *printable* char, incl. the space
## `strlen`
Given a valid string, i.e. a NULL-terminated char array, calculate its length, excluding the null byte at the end
## `memset`
```c
void    *ft_memset(void *s, int c, size_t n)
```
fill the `n` first bytes of memory pointed to by `s` with the constant byte `c`
## `bzero`
```c
void    ft_bzero(void *s, size_t n)
```
erase all the data in the first `n` bytes starting at `s` by writing zeros to that area

>[!observation]
>it's like doing a `memset` where the passed `c` is 0


## `memcpy`
```c
void    *ft_memcpy(void *dest, const void *src, size_t n);
```
copies `n` bytes from the memory starting at `src` to the memory starting at `dest`

>[!danger] the memory areas must not overlap!

### impl. notes
- you may not do anything if both `dest` & `src` are pointing to `NULL`
- when you're copying each byte, you can just call `memset` for each byte
	- convert whatever is in `src` to an unsigned char and then into an int so that `memset` can take it
## `memmove`
```c
void    *ft_memmove(void *dest, const void *src, size_t n)
```
It's like a `memcpy` but overlapping memory is allowed. Basically it's like a `memcpy` but copying from the n-th byte to the first.

## `strlcpy`
```c
size_t  ft_strlcpy(char *dest, const char *src, size_t size)
```

Copy up to `size - 1` chars from `src` to `dest`. 

### impl. notes
- make sure to always NULL-terminate the str (if `size > 0`)
- a byte for the NULL termination char is included in `size`
- only works with *valid* strings (NULL-terminated char arrays) i.e. both `src` & `dest` must be NULL-terminated
- return the length of `src`

## `strlcat`
```c
size_t  ft_strlcat(char *dst, const char *src, size_t size)
```
appends  the NUL-terminated string `src` to the end of `dst`.  It will append at most `size - strlen(dst) - 1` bytes, NUL-terminating the result.
### impl. notes
- if `size < len(dest)` => copy nothing & return `i + len(src)`
>"*if strlcat() traverses size characters without finding a NUL, the length of the string is considered to be size and the destination string will not be NUL-terminated (since there was no space for the NUL)*"  - `man strlcat`
- else, return `len(dest) + len(src)`

## `toupper`
Given an unsigned char, if it's a lowercase => make it uppercase

## `tolower`
idem but in reverse

## `strchr`
```c
char    *ft_strchr(const char *s, int c)
```
return a pointer to the first occurrence of the character `c` in the string `s`

## `strrchr`
```c
char    *ft_strrchr(const char *s, int c)
```
idem, but with the **last** occurrence

## `strncmp`
```c
int ft_strncmp(const char *s1, const char *s2, size_t n)
```

compares the `n` first bytes (alt. chars) two strings `s` and `s2`.

>[!warning] comparison is done using unsigned chars

## `memchr`
```c
void    *ft_memchr(const void *s, int c, size_t n)
```
scan the initial `n` bytes of the memory area pointed to by `s` for the first instance of `c`.  

>[!warning] `c` & the bytes of `s` are interpreted as unsigned chars


## `memcmp`
```c
int ft_memcmp(const void *s1, const void *s2, size_t n)
```

compare the first `n` bytes of the memory areas `s1` & `s2`
>[!warning] the bytes of `s1` & `s2` are interpreted as unsigned chars

## `strnstr`
```c
char    *ft_strnstr(const char *big, const char *little, size_t len)
```
locate the first occurrence of the nul-terminated string `little` in the string `big`, where not more than `len` chars are searched

>[!warning] chars appearing after a `\0` char are not searched

>[!info] return values (from docs)
> - if little is an empty string => big is returned
> - if little occurs nowhere in big => NULL is returned
> - otherwise a pointer to the first character of the first occurrence of little is returned
## `atoi`
```c
int ft_atoi(const char *nptr)
```

char to int

ignore however many "whitespaces" there are in your string, where a whitespace is one of the following ASCII chars:
- `\t` *horizontal tab*
- `\r` *carriage return* - a control character in the ASCII character set used to move the cursor to the beginning of the line in a text editor or terminal
- ` ` (normal space)
- `\f` *form feed* - used to advance the cursor or print head to the next page or form
- `\v` *vertical tab* - used in ye olde times to move quick vertically
- `\n` *next line*


---

>[!danger] dynamic memory allocation
> now, whenever you want to use `malloc`, you need to check every time you call it to check if it worked OK
> you check whether the returned pointer by `malloc` is NULL and if it is => exit the function
## `calloc`
```c
void    *ft_calloc(size_t nmemb, size_t size)
```

like a `malloc` and then initialize every allocated byte to 0/NULL
### impl. notes
you can observe that you can just do a `malloc` and call `bzero` on the newly allocated mem

## `strdup`
```c
char    *ft_strdup(const char *s)
```
return a pointer to a new string which is a duplicate of `s`

### impl. notes
- notice that we can call `memcpy` to do the copying
	- [!] you must pass the length of s **+1** though, cause the size needs to include `\0` for `memcpy`

# additional methods
(check pdf for these, quicker)
## `substr`
given a string `s`, create a sub-string that starts at the position `start` of `s` & up to the next `len` chars
### impl. notes
- if you start counting from the position `start` and the amount of chars at the end of `s` are less than the amount required by `len` => we recalculate `len` to stop at the end of `s` and avoid copying garbage
- once we are ready to copy, we can just call `strlcpy`

## `strjoin`
```c
char    *ft_strjoin(char const *s1, char const *s2);
```
given 2 strings, create a new one which is the concatenation of `s1` & `s2`
### impl. notes
>[!info] empty string
>can be represented as `""`, i.e. a single-char string whose value is 0

- we can just call `strdup` for the edge cases
	- if both strings are empty strings => empty string
	- if either is an empty string => return a copy of the other one
- in the "good path" we
	- calculate both lengths to figure out how much we need to reserve in memory
	- copy the first string into the new one with `strlcpy`
	- concatenate the 2nd one with `strlcat`
## `strtrim`
```c
char    *ft_strtrim(char const *s1, char const *set)
```
create a new string by eliminating from the front & back of `s1` all the chars in the string `set`

### impl. notes
- we calculate 2 positions `start` & `end` to figure out which inner position delimit the sub-string of `s1` which we need to copy & then we call `substr`

## `split`
```c
char    **ft_split(const char *s, char c)
```
return an array of strings resulting from separating `s` by the character `c`

### impl. notes
>[!info] i defined a "*word*" as each of the resulting strings in the resulting array

i used additional methods here
1. `ft_count_words` to figure out how long the resulting array of strings should be
2. `ft_fill_words` to loop over `s` and allocate the words
	the idea is to loop over the separation char until you find the start of a "word" and calculate its length
3. `ft_alloc_word` once you find the start of a word, try to allocate it and copy its content from `s`

>[!warning]
>in case a word allocation fails, which is checked in `ft_fill_words`, you must call `ft_free_str_array` to free every word allocated already and the resulting array

## `itoa`
```c
char    *ft_itoa(int n);
```
reverse of `atoi`, return a dynamically allocated string with the given number in base 10

## `strmapi`
```c
char    *ft_strmapi(char const *s, char (*f)(unsigned int, char));
```
return a new string resulting from applying the function `f` with signature 

```c
char f(unsigned int, char)
```
to every character in `s` where 
- the unsigned int is the index of that char
- the char is the char itself

## `striteri`
```c
void    ft_striteri(char *s, void (*f)(unsigned int, char *))
```
similar to `strmap` but here the `f` function gets the pointer to the char instead of the value, so that it can be modified instead of creating a new char

(easy functions here)


## `putnbr`
like a `itoa` but printing the number instead of storing it as a string in memory
>[!warning] you're only allowed to use `write`, not `malloc`!

# bonus
## `lstnew`
given a `content`, create a node by passing the content in the argument, and setting `next` to NULL
```c
t_list  *ft_lstnew(void *content)
```

## `lstadd_front`
given the position of a node `lst`, add a given node `new` at the front
```c
void    ft_lstadd_front(t_list **lst, t_list *new)
```

## `lstsize`
```c
int     ft_lstsize(t_list *lst);
```
calculate the amount of nodes on a given list
### impl. notes
you may loop over a list by continuously accessing the `next` node until `next` is `NULL`

## `lstlast`
