---
{"dg-publish":true,"permalink":"/🖥/🐧/files/file descriptors/","tags":["c","cpp"]}
---



*in Unix-type systems,*
>[!definition] file descriptor
> a small positive integer used as a reference to an open file in a process

>[!warning] a "*file*" is not only a text file
>it can also be
>- a directory
>- other input/output resources e.g.
>	- a keyboard
>	- a screen
>	- a pipe
>	- a network socket

therefore, any process inherits
# default open file descriptors

| fd  | name                | `<unistd.h>`    | `<stdio.h>` |
| --- | ------------------- | --------------- | ----------- |
| 0   | standard **input**  | `STDIN_FILENO`  | `stdin`     |
| 1   | standard **output** | `STDOUT_FILENO` | `stdout`    |
| 2   | standard **error**  | `STDERR_FILENO` | `stderr`    |
>[!info] [[🖥/🐧/files/representation of open files\|representation of open files]]

