---
{"dg-publish":true,"permalink":"/🖥/🛠/🕸networks/logical volumes vs logical partitions/","tags":["unix"]}
---


# logical volumes

>[!definition] logical volume
>logical volumes are a feature of the **Logical Volume Manager** (**LVM**), which is a powerful system for managing disk storage in Linux

with LVM, you can create *logical volumes* s.t.
- span multiple physical disks
- dynamically resize them as needed
- provide flexibility in managing storage space
- simplify tasks, e.g. resizing partitions or migrating data btwn disks

## key points about logical volumes

- *volume groups*: logical volumes are created with these, which consist of 1+ *physical volumes* (actual disks or disk partitions)
- *spanning across physical volumes*: logical volumes can span multiple physical volumes => efficient use of disk space across multiple disks
- *dynamic resizing*: one of the primary advantages of logical volumes.
	I.e., administrators can adjust the size of logical volumes on-the-fly.
	- [i] particularly valuable in environments where storage requirements are subject to change
- *snapshots and thin provisioning*: LVM provides features like *snapshots*, which allow point-in-time copies of logical volumes, and thin provisioning, which allows you to allocate storage space dynamically as needed
	- [i] *thin provisioning*: involves using virtualization technology to give the appearance of having more physical resources than are actually available. if a system always has enough resource to simultaneously support all of the virtualized resources => it is not thin provisioned
- *performance enhancement with striping*: LVM also supports striping, which distributes data across multiple Physical Volumes to improve performance.  
- *tools for managing logical volumes*: logical volumes are managed using tools like `lvcreate`, `lvextend`, `lvresize`, etc. within the LVM framework
- *use cases*: logical volumes are commonly used in enterprise environments and systems where dynamic storage management and where flexibility and scalability are important
![Pasted image 20250201175548.png](/img/user/Pasted%20image%2020250201175548.png)
(PV: Physical Volume; VG: Volume Group; LV: Logical Volume)

# Logical Partitions

>[!definition] logical partition
> logical partitions are a feature of the traditional **Master Boot Record** (**MBR**) partitioning scheme. 
> they are used to overcome the limitation of four primary partitions per disk by creating *extended partitions* that can host multiple *logical partitions* within them

## key points about logical partitions

- *extended partitions*: logical partitions are created within *extended partitions* and are primarily used to overcome the limitation of 4 primary partitions per disk.
	an extended partition is a special type of primary partition that can hold multiple logical partitions
- **Master Boot Record**: the **MBR** partitioning scheme traditionally supports up to 4 primary partitions. to overcome this limitation and create more than four partitions, one of the primary partitions can be designated as an extended partition. it operates effectively with disks of up to a maximum size of `2TB`
- *single disk span limitation*: unlike logical volumes, logical partitions **cannot** span multiple physical disks
- *tools for managing logical partitions*: logical partitions are managed using tools like `fdisk`, `parted ...`, typically within the context of the MBR partition table
- *use cases*: logical partitions are still used in many scenarios, and are commonly used in legacy systems that rely on MBR partitioning. they provide a straightforward method for partitioning disks without the need for advanced management features offered by LVM or where LVM is not preferred or necessary.
![Pasted image 20250201181108.png](/img/user/Pasted%20image%2020250201181108.png)
[🔗source](https://www.minitool.com/lib/logical-partition.html)

