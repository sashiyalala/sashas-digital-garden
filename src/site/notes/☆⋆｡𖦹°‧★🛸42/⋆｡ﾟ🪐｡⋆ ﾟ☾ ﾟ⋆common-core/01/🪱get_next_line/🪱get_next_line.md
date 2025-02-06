---
{"dg-publish":true,"permalink":"/☆⋆｡𖦹°‧★🛸42/⋆｡ﾟ🪐｡⋆ ﾟ☾ ﾟ⋆common-core/01/🪱get_next_line/🪱get_next_line/","tags":["42madrid","c","common-core","milestone1"]}
---


>[!location]
>```sh
>/home/facosta/sgoinfre/workspace/m1/ws_get_next_line
>```

>[!repo]
>```sh
>git@vogsphere-v2.42madrid.com:vogsphere/intra-uuid-66f8c416-cfa0-4591-a68a-f450ec3e6281-6259239-facosta
>```
>alt. ([[☆⋆｡𖦹°‧★🛸42/⋆˖⁺‧₊☽◯☾₊‧⁺˖⋆meta/workflow/🐈‍⬛🐙🚀 my git remotes @ 42\|🐈‍⬛🐙🚀 my git remotes @ 42]]):
>```sh
>git@git.42:vogsphere/intra-uuid-66f8c416-cfa0-4591-a68a-f450ec3e6281-6259239-facosta
>```

# subject
- calling `get_next_line` repeatedly (e.g. with a loop) will let you read the contents of the file to which the file descriptor is pointing to, **line by line**, until the end
- the method must return the line just read. if there is nothing more to read or an error happened, return ``NULL``
- make sure the method behaves correctly when reading from either a file or [[🖥/📜/🍊C/😮 stdin\|😮 stdin]]
- take into account that the returned line must finish with the character `\n`, except if the end of the file has been reached, which doesn't end with `\n`
- in the header `get_next_line.h` you must *at least* have the prototype of the method `get_next_line`
- add all helpful methods you might need to the file `get_next_line_utils.c`

