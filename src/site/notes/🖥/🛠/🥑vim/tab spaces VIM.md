---
{"dg-publish":true,"permalink":"///vim/tab-spaces-vim/","tags":["vim"]}
---


- one-time in terminal: `:set ts=4 sw=4`
- to have it always by default:
	- create a file in your home directory called `~.vimrc` and add this
```bash
set tabstop=4 shiftwidth=4
```