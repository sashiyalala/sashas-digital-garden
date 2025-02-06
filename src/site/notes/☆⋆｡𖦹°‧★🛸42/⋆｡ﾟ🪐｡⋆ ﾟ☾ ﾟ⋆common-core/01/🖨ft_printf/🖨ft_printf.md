---
{"dg-publish":true,"permalink":"/☆⋆｡𖦹°‧★🛸42/⋆｡ﾟ🪐｡⋆ ﾟ☾ ﾟ⋆common-core/01/🖨ft_printf/🖨ft_printf/","tags":["42madrid","c","common-core","milestone1"]}
---



>[!location]
> ```
> /home/facosta/sgoinfre/workspace/m1/ws_ft_printf
> ```


>[!repo]
>```sh
>git@vogsphere-v2.42madrid.com:vogsphere/intra-uuid-37017c37-f279-43c5-86b7-f629581e8a9b-6259240-facosta
>```
>alt. ([[☆⋆｡𖦹°‧★🛸42/⋆˖⁺‧₊☽◯☾₊‧⁺˖⋆meta/workflow/🐈‍⬛🐙🚀 my git remotes @ 42\|🐈‍⬛🐙🚀 my git remotes @ 42]]):
>```sh
>git@git.42:vogsphere/intra-uuid-37017c37-f279-43c5-86b7-f629581e8a9b-6259240-facosta
>```


# subject
- No implementes la gestión del buffer del `printf()` original.
- Deberás implementar las siguientes conversiones: `cspdiuxX %`
- Tu función se comparará con el `printf()` original.
- Tienes que usar el comando `ar` para crear tu librería. El uso de `libtool` está prohibido.
- Tu archivo `libftprintf.a` deberá ser creado en la raíz de tu repositorio.
# conversiones
Tienes que implementar las siguientes conversiones:
- `%c` Imprime un solo carácter.
- `%s` Imprime una string (como se define por defecto en C).
- `%p` El puntero void `*` dado como argumento se imprime en formato hexadecimal.
- `%d` Imprime un número decimal (base 10).
- `%i` Imprime un entero en base 10.
- `%u` Imprime un número decimal (base 10) sin signo.
- `%x` Imprime un número hexadecimal (base 16) en minúsculas.
- `%X` Imprime un número hexadecimal (base 16) en mayúsculas.
- `%%` para imprimir el símbolo del porcentaje.
# bonus

lista de posibles bonus:
- Gestiona cualquier combinación de los siguientes flags: `’-0.’` y el ancho mínimo (*field minimum width*) bajo todas las conversiones posibles.
- Gestiona todos los siguientes flags: `’# +’` (sí, uno de ellos es un espacio)