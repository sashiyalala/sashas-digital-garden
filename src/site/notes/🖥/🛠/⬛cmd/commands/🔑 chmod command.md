---
{"dg-publish":true,"permalink":"/🖥/🛠/⬛cmd/commands/🔑 chmod command/","tags":["unix"]}
---


>[!warning] chmod doesn't change permissions of symbolic links

The format of a symbolic mode is, where perms is
       either  zero  or more letters from the set `rwxXst`, or a single letter from the
       set `ugo`.  Multiple symbolic modes can be given, separated by commas.
```bash
 [ugoa...][-+=][perms...]
```

## ugoa
- u - file owner
- g - other users in the file's group
- o - other
- a - all users (default if none given)

## operator
- + - selected file mode bits are **added** to the existing file mode bits
- "-" - file mode are removed
- "=" - causes file mode bits to be added and causes unmentioned bits to be rm'd 

## rwxXst
- r - read
- w - write
- x - execute (or search for dirs)
- X - execute/search only if the file is a directory or already has execute permission for some user
- s - set user or group ID on execution
- t - restricted deletion flag or "sticky bit" (can only be set on dirs) if enabled => restricts the ability to delete or rename files within that directory to the file owner

```bash
chmod <permissions> <list_of_files>
```

- *permissions* - 3-digit 8al number ("ABC") that correspond to the [[🖥/🛠/⬛cmd/commands/🕵file permissions\|🕵file permissions]] of the user who owns the file, the group and other users such that
	- A + B + C = 4 if read permission
	- A + B + C = 2 if write permission
	- A + B + C = 1 if execute permission 