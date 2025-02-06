---
{"dg-publish":true,"permalink":"/🖥/🐧/files/representation of open files/","tags":["programming","unix"]}
---




to represent open files, the system uses 3 data structs:
- **table of file descriptors**
	- 1x per process
	- each record == an idx
- **inode(index node) table**
	- **shared** btwn **all** processes
	- ea. entry describes the file in detail:
		- path to its location on disk
		- size
		- permissions
		- ...
- **open file table**
	- **shared** btwn **all** processes
	- ea. entry for each file, among other infos:
		- access mode
		- offset, i.e. current location within the file
		- pointer to corresponding entry in *inode table*