---
{"dg-publish":true,"permalink":"/🖥/🛠/🕸networks/lsblk/","tags":["unix"]}
---


>[!definition]  `lsblk` (list block devices)


# usage

running it without any options will list all block devices in a *tree-like* format

```sh
$ lsblk  
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT  
sda      8:0    0 238.5G  0 disk  
├─sda1   8:1    0   512M  0 part /boot/efi  
└─sda2   8:2    0   238G  0 part /
```

| column name | desc                                                                                                                                                                                                                                                                            |
| ----------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| NAME        | device name                                                                                                                                                                                                                                                                     |
| MAJ:MIN     | major and minor device number (major identifies the driver, i.e., disk drive, floppy disk...) and the minor device number identifies the specific device, i.e., the first floppy would have minor '0', the second would be '1',...they tell the kernel how to access the device |
| RM          | whether the device is removable or not (1 if true)                                                                                                                                                                                                                              |
| SIZE        | size of the device                                                                                                                                                                                                                                                              |
| RO          | whether the device is read-only (1 if true)                                                                                                                                                                                                                                     |
| TYPE        | type of device (disk, partition, etc.)                                                                                                                                                                                                                                          |
| MOUNTPOINT  | device's mount point (if available)                                                                                                                                                                                                                                             |

## some options

`-l` lists the output in a list format

```sh
$ lsblk -l  
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT  
sda      8:0    0 238.5G  0 disk  
sda1     8:1    0   512M  0 part /boot/efi  
sda2     8:2    0   238G  0 part /
```


and `-f` includes *file-system* information in the output

```sh
$ lsblk -f  
NAME   FSTYPE LABEL UUID                                 MOUNTPOINT  
sda  
├─sda1 vfat         1234-5678                            /boot/efi  
└─sda2 ext4         12345678-1234-1234-1234-123456789012 /
```
## other supported parameters

- `-b` displays the size of the blocks in bytes.
- `-m` provides a more human-readable format, displaying sizes in powers of 1024.
- `-a` shows all block devices, including empty ones.
- `-p` includes the full path of each device in the output.
- `-r` produces raw output, suitable for use in scripts.
- `-o <columns>` to retrieve just specific columns, e.g., `lsblk -o NAME,SIZE`


>[!warning]
> be aware that the `lsblk` command only shows block devices. if you are interested in other types of devices, such as character devices or network interfaces, you will need to use other tools
>
