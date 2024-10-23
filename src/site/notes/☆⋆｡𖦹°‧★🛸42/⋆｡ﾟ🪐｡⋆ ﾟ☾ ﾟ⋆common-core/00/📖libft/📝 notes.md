---
{"dg-publish":true,"permalink":"/☆⋆｡𖦹°‧★🛸42/⋆｡ﾟ🪐｡⋆ ﾟ☾ ﾟ⋆common-core/00/📖libft/📝 notes/","tags":["42madrid","c","common-core","circle0"]}
---



- in the header ``libft.h`` I do `# include <stddef.h>` instead of any other library cause it's the library where the `size_t` type is declared
	- if I need `malloc`, I'll include the appropriate header whenever I need to call that function specifically. I don't need it for my prototypes in the library header


# memcpy vs memmove
memcpy doesn't support overlap btwn `src` & `dest`, while memmove does.

the idea is that memcpy starts copying from left to right & memmove, backwards

