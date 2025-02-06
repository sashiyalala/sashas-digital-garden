---
{"dg-publish":true,"permalink":"/🖥/📜/🍊C/random/valgrind/","tags":["c","cheat","cpp"]}
---


```c
valgrind --leak-check=full \
         --show-leak-kinds=all \
         --track-origins=yes \
         --verbose \
         --log-file=valgrind-out.txt \
         ./executable exampleParam1
```

>[!example] for me 👀
>```c
> valgrind --leak-check=full \
>         --show-leak-kinds=all \
>         --track-origins=yes \
>         --verbose \
>         --log-file=valgrind-out.txt \
>         ./main
> ```

>[!link] [🔗another guide to learn how to use valgrind:)](https://www.it.uc3m.es/pbasanta/asng/course_notes/memory_profiler_en.html)

in short:

- `--leak-check=full` each individual leak will be shown in detail
- `--show-leak-kinds=all` show all of "definite, indirect, possible, reachable" leak kinds in the "full" report
- `--track-origins=yes` favour useful output over speed. this tracks the origins of uninitialised values, which could be very useful for memory errors. 
	- [i] consider turning off if *valgrind* unacceptably slow
- `--verbose` can tell you about unusual behaviour of your program. repeat for *more* verbosity
- `--log-file` write to a given log file. useful when output too long to fit/review over terminal


>[!question] I have a leak, but *WHERE*?
> go to the source link :)

