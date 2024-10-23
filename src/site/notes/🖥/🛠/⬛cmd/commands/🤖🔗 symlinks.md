---
{"dg-publish":true,"permalink":"/🖥/🛠/⬛cmd/commands/🤖🔗 symlinks/","tags":["unix","cheat"]}
---


>[!info] **hard** links
>created like symlinks but without `-s`
>NOTE how they're the number in the 2nd col of the [[🖥/🛠/⬛cmd/commands/📃 list\|📃 list]] command
# explanation
```bash
lrwxr-xr-x  1 root  wheel  54 May  8 15:37 /usr/local/bin/docker -> /Applications/Docker.app/Contents/Resources/bin/docker
```

the `->` symbol in `some/fi/le -> /another/file` means that the type of file of `some/fi/le` is a **symbolic link**

the file `le` is the actual link and `/another/file` is the linked file, the real archivo.

# create symlink
## by default
```bash
$ ln -s /home/facosta/workspace/shell_00/shell00/ex02/total0 test6
$ ls -l
drwx--xr-x 2 facosta 2024_madrid 20 Aug  5 15:00 test0
lrwxrwxrwx 1 facosta 2024_madrid 52 Aug  5 15:02 test6 -> /home/facosta/workspace/shell_00/shell00/ex02/total0
```
 will display with full path
## to just display rel path
the same but with an "r"!
```bash
$ ln -rs /home/facosta/workspace/shell_00/shell00/ex02/total0 test6
$ ls -l
drwx--xr-x 2 facosta 2024_madrid 20 Aug  5 15:00 test0
lrwxrwxrwx 1 facosta 2024_madrid  6 Aug  5 15:04 test6 -> total0
```

# edit last modified time in symlinks
You need to use `-h` like this:

```bash
$ ls -l
total 16
drwx--xr-x 2 facosta 2024_madrid 19 Jun  1 22:20 test0
lrwxrwxrwx 1 facosta 2024_madrid  5 Aug  5 15:27 test6 -> test0
$ touch -hm --date="2024-06-01 22:20" test6
$ ls -l
total 16
drwx--xr-x 2 facosta 2024_madrid 19 Jun  1 22:20 test0
lrwxrwxrwx 1 facosta 2024_madrid  5 Jun  1 22:20 test6 -> test0
$ touch -m --date="2024-06-01 20:47" test0 
$ ls -l
total 16
drwx--xr-x 2 facosta 2024_madrid 19 Jun  1 20:47 test0
lrwxrwxrwx 1 facosta 2024_madrid  5 Jun  1 22:20 test6 -> test0 
```

