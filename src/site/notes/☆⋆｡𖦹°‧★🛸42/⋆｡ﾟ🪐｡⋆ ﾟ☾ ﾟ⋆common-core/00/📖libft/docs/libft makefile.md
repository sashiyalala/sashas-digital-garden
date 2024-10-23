---
{"dg-publish":true,"permalink":"/☆⋆｡𖦹°‧★🛸42/⋆｡ﾟ🪐｡⋆ ﾟ☾ ﾟ⋆common-core/00/📖libft/docs/libft makefile/","tags":["makefile","c","42madrid"]}
---

# targets
usually a target looks like this
```makefile
targets: prerequisites
	command
	command
	...
```
where a prerequisite is a file that must exist before executing the commands of a specific target
## the `all` target
>[!definition] `all`
>the default target used to build the main product of the compilation process

```makefile
all: $(NAME) clean
	...
```
when running `make all`, the target checks if the file defined in the variable `NAME` exists:
- ✔ -> nothing
- ❎ -> moves to the next line
```makefile
$(NAME): $(OFILES)
	ar rcs $(NAME) $(OFILES)
```

1. Does file with name `$(NAME)` exist?
	- ✔ -> nothing
	- ❎ -> go to next line. All files in `$(OFILES)` exist?
		- ✔ -> makefile uses [[🖥/📜langs/🍊C/makefile/the ar command\|the ar command]] to create the *archive* file which will become our static library

>[!important] 
> I won't include the `s` flag to the `ar` command just in case for this project.

>[!info] changing the *default* target
>by using the `.DEFAULT` target we can declare which target is run when simply running `make`

## the `.PHONY` target
>[!definition] `.PHONY`
>a target to tell `make` that those targets are not associated to any files, so no need to check that. Just actions to be run.
>Use this to avoid unexpected behaviour