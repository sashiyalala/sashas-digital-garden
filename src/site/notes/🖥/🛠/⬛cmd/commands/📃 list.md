---
{"dg-publish":true,"permalink":"/🖥/🛠/⬛cmd/commands/📃 list/","tags":["cheat","unix"]}
---


# the list command
```bash
ls
```

# -a: all
including hidden (start with `.` ) files
# -F: full listing
indicates what type files are by putting a slash after directories and a star after executable files (the programs you can run) 
# -R: recursive listing
includes content of subdirs
# -t: ordered listing
by time when they were last modified (newest first)
# -r: reverse order listing

>[!tip] `ls -lrt`
> a long listing, oldest first ordered list of your files
# -l: the long listing format

```bash
$ ls -l
drwxr-xr-x   6 eva        users         1024 Jun  8 16:46 sabon
-rw-------   1 eva        users         1564 Apr 28 14:35 splus
-rw-------   1 eva        users         1119 Apr 28 16:00 splus2
-rw-r--r--   1 eva        users         9753 Sep 27 11:14 ssh_known_hosts
-rw-r--r--   1 eva        users         4131 Sep 21 15:23 swlist.out
-rw-r--r--   1 eva        users        94031 Sep  1 16:07 tarnti.zip
```

1. the type of file (dir or file) & [[🖥/🛠/⬛cmd/commands/🕵file permissions\|🕵file permissions]]
2. number of **hard** links to the file - number of names there're for the file. [[🖥/🛠/⬛cmd/commands/🤖🔗 symlinks\|🤖🔗 symlinks]] are not counted
3. user who owns the file
4. Unix group of users to which the file belongs
5. size of the file in bytes
6. 7 & 8.: the time at which a file was last changed (alt. a file in that dir that was last created/changed)
9. name of the file
# -m: with commas
lists all files in a single line, separated by comma and space