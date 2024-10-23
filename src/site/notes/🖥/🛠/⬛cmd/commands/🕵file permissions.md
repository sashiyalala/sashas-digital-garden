---
{"dg-publish":true,"permalink":"/🖥/🛠/⬛cmd/commands/🕵file permissions/","tags":["cheat","unix"]}
---


check out a file's permissions with 
```bash
$ ls -l <filename>

$ ls -l my_file
-rw-r--r-- 1 facosta 2024_madrid 17 Aug  5 12:06 testShell00
```

# file permissions legend

| part |           | length(chars) | values                                                                 |
| ---- | --------- | ------------- | ---------------------------------------------------------------------- |
| -    | file type | random        | "-" file / "d" for directory / other various letters for obscure types |
| rw-  | user      | 3             | permissions for file owner user                                        |
| r--  | group     | 3             | permissions for group which owns the file                              |
| r--  | other     | 3             | permissions for all other users                                        |
### permissions

the permissions for the 3 groups (user/group/others) are always 3 chars with this structure.

>[!warning]
> if there is a "-" that means you don't have that permission

|       | name    | file                          | dir                                      |
| ----- | ------- | ----------------------------- | ---------------------------------------- |
| **r** | read    | can read the file             | can list files in the directory          |
| **w** | write   | can edit the file             | can create/delete files in the directory |
| **x** | execute | can run the file as a program | can *change* to the directory            |


# change file permissions
with the [[🖥/🛠/⬛cmd/commands/🔑 chmod command\|🔑 chmod command]]