---
{"dg-publish":true,"permalink":"/☆⋆｡𖦹°‧★🛸42/⋆｡ﾟ🪐｡⋆ ﾟ☾ ﾟ⋆common-core/01/🌱born2beroot/📝eval/📚notes/virtual machine/","tags":["42madrid","virtual","unix"]}
---


>[!definition] virtual machine (VM)
> a VM is software that simulates the behaviour of a real machine with physical resources, like a laptop, smart phone, server, etc.
> it's represented by a computer file, usually called *image*, which is run by another piece of software


>[!definition] virtualization
>process of creating a VM. 

- [i] has the same resources as a laptop, smart phone or server: CPU, memory, disks to store files...
	-> but instead of being hardware, they're generated as software running on/*borrowed* set of physical resources
- [i] a VM is *partitioned* from the rest of the system it's running from, i.e. the software can't interfere with the host computer's primary OS
- [i] its resources are a dedicated CPU, memory, storage... which are *borrowed* from a physical *host* computer, e.g., laptop, server, data-center...

# usages
- backing up an existing OS
- specially, images, are used to easily move or run the same machine on different machines, e.g. if you have different laptops you can just carry your image in a pendrive and "mostly" not care about the physical machine you're working on
- offering an already set up environment for, e.g. devs
- trying out software you're not sure about, on a specific environment
- try out (possibly) unsafe software
