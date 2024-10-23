---
{"dg-publish":true,"permalink":"/🖥/📜langs/🍊C/makefile/the ar command/","tags":["42madrid","c","makefile","shell"]}
---


### the `ar` command
>[!definition] `ar`
>a command used to combine 1+ file/s into a single *archive* file

check out the source to see all possible flags.
## some important flags
- `r` *replace* - replace or add files to the archive
- `c` *create* - create the archive file if it doesn't exist
- `s` *index the archive* - write an index into the archive **for faster searches** 
>[!tip] generally good to add `s` for static libs with `ar`
>specially if there are many `.o` files