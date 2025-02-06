---
{"dg-publish":true,"permalink":"/🖥/📜/🍊C/📘fcntl/read/","tags":["c","programming"]}
---


>[!definition] read
> ```c
> ssize_t read(int fildes, void *buf, size_t nbyte);
> ```
> attempts to read `nbyte` bytes of data from the object referenced by the `fildes` [[🖥/🐧/files/file descriptors\|file descriptor]] and stores the bytes in the reference `buf`.


if anything during the read fails => returns a **negative value**

>[!tip] a way to do an initial check for reading is to do this:
>```c
> read(fd, NULL, 0);
>```
>NOTE: passing `NULL` means that we don't store the "read" bytes anywhere.
> this can be done to check that there is data ready to be read and that the `fd`([[🖥/🐧/files/file descriptors\|file descriptor]]) is ready to be read from, by not really reading anything :)
> if everything is alright, you should get `0`, otherwise it means something is wrong 😰







