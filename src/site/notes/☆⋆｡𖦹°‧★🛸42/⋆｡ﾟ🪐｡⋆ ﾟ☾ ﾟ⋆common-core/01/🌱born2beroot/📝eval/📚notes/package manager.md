---
{"dg-publish":true,"permalink":"/☆⋆｡𖦹°‧★🛸42/⋆｡ﾟ🪐｡⋆ ﾟ☾ ﾟ⋆common-core/01/🌱born2beroot/📝eval/📚notes/package manager/","tags":["unix","42madrid"]}
---



>[!definition] package manager 
>collection of software tools to automate the process of installing, upgrading, configuring(version, storage) and removing packages y/o dependencies


# APT
for Debian-based systems


cool link to learn: [🔗cool reddit response to learn](https://www.reddit.com/r/debian/comments/9whj01/comment/e9q2bd2/?utm_source=share&utm_medium=web3x&utm_name=web3xcss&utm_term=1&utm_content=share_button)
los paquetes vienen en 2 opciones
- source (pasan2)
- binario - archivos `ar` que contienen 2 subarchivos
	- `control.tar.gz` archivos de control: 
	- `data.tar.XX` (típicamente `xz`)
	- (además) un archivo `debian-binary` que lleva la versión del paquete 
# DNF
for Rocky OS