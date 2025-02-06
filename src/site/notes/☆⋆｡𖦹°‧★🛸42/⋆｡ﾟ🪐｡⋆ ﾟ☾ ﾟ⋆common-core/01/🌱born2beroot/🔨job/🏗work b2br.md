---
{"dg-publish":true,"permalink":"/☆⋆｡𖦹°‧★🛸42/⋆｡ﾟ🪐｡⋆ ﾟ☾ ﾟ⋆common-core/01/🌱born2beroot/🔨job/🏗work b2br/","tags":["42madrid","unix","milestone1","virtual"]}
---


- [i] hecho con [VirtualBox](https://github.com/gemartin99/Born2beroot-Tutorial/tree/main?tab=readme-ov-file#2-1-instalaci%C3%B3n-de-la-m%C3%A1quina-con-virtual-box-)


link para descargar la ISO de la última versión de Debian **estable**: https://www.debian.org/download 

para el trabajo elegí seguir esta guía online (para solo la parte mandatoria): 
[🔗video](https://www.youtube.com/watch?v=s2eM7L_etzo)

![Pasted image 20250201193145.png](/img/user/Pasted%20image%2020250201193145.png)

root password: enderman
password for facosta user: XXX
encryption passphrase: XXX

server configuration: https://www.youtube.com/watch?v=3Vw0HlJHLTQ


# helpful commands during server configuration

## installing & configuring `sudo`

- **s**witch **u**ser to root (fast)
```sh
su -
```
- the `sudo` cmd is configured re. a file under `/etc/sudoers`

>[!danger] **never** edit the `/etc/sudoers` file with a text editor. 
>**always use** `visudo` (it opens a text editor but checks the syntax on save)

>[!tip] more info about `visudo` [🔗here](https://www.digitalocean.com/community/tutorials/how-to-edit-the-sudoers-file-es)

this is what I added to my `/etc/sudoers`:
![Pasted image 20250202131722.png](/img/user/Pasted%20image%2020250202131722.png)

## installing and configuring [[☆⋆｡𖦹°‧★🛸42/⋆｡ﾟ🪐｡⋆ ﾟ☾ ﾟ⋆common-core/01/🌱born2beroot/📝eval/📚notes/SSH service\|ssh]]

- to install:
```sh
apt install openssh-server -y
```
- to configure, edit the file `/etc/ssh/sshd_config` (specifies the locations of one or more host key files (mandatory) and the location of authorized_keys files for users, among many other files)

here is the final result:
![Pasted image 20250202133035.png](/img/user/Pasted%20image%2020250202133035.png)
- changed SSH port to 4242
- changed `PermitRootLogin` to `no` to disable connecting via SSH with `root`

- use this command to check the status of the SSH service
```sh
sudo service ssh status
```
- and this one to restart it so the changes in the config file take place
```sh
sudo service ssh restart
```

and now we can see that it now runs on `4242` after restart
![Pasted image 20250202134126.png](/img/user/Pasted%20image%2020250202134126.png)

## installing and configuring [[☆⋆｡𖦹°‧★🛸42/⋆｡ﾟ🪐｡⋆ ﾟ☾ ﾟ⋆common-core/01/🌱born2beroot/📝eval/📚notes/UFW\|UFW]]

- to install ufw
```sh
sudo apt install ufw
```
- to "turn it on" enable it
```sh
sudo ufw enable
```

to edit firewalls and ports, you add/remove "*rules*"
- e.g., to allow port 4242:
```sh
sudo ufw allow 4242
```
- check all your current rules with this command
```sh
sudo ufw status
```

thus, I only have rules for port 4242:
![Pasted image 20250202145943.png](/img/user/Pasted%20image%2020250202145943.png)

## connecting to the [[☆⋆｡𖦹°‧★🛸42/⋆｡ﾟ🪐｡⋆ ﾟ☾ ﾟ⋆common-core/01/🌱born2beroot/📝eval/📚notes/virtual machine\|vm]] via [[☆⋆｡𖦹°‧★🛸42/⋆｡ﾟ🪐｡⋆ ﾟ☾ ﾟ⋆common-core/01/🌱born2beroot/📝eval/📚notes/SSH service\|ssh]]

### ssh connection **inside** the vm terminal on port 4242

```sh
ssh facosta@127.0.0.1 -p 4242
```

### ssh connection from **outside** the vm terminal on port 4242
first go to the settings here and click "Port Forwarding"
![Pasted image 20250202150527.png](/img/user/Pasted%20image%2020250202150527.png)

and add a new rule just filling out 
- Host Port: 4242
- Guest Port: 4242

Now,
- check if port 4242 is listening to connections from the outside with
```sh
netstat -tuln | grep 4242
```

>[!success]
>```sh
>➜  ~ netstat -tuln | grep 4242
>tcp        0      0 127.0.0.1:4242          0.0.0.0:*                LISTEN
>```

and try the same command from outside
```sh
ssh facosta@127.0.0.1 -p 4242
```

>[!warning]
> if you get this error:
> ```sh
> ➜  ~ ssh facosta@127.0.0.1 -p 4242
kex_exchange_identification: Connection closed by remote host
Connection closed by 127.0.0.1 port 4242
> ```
> change the Host Port to 4241 and try again 

this works :)

```sh
ssh facosta@127.0.0.1 -p 4241
```

## password policy

this gets configured in the file `/etc/login.defs`
open it with whatever editor you want

- password expires in 30 days with a 2-day minimum change limit and a 7-day warning
![Pasted image 20250202152117.png](/img/user/Pasted%20image%2020250202152117.png)
and save :)

- install the password quality checking library
```sh
sudo apt-get install libpam-pwquality -y
```
- [i] this package stores previous passwords so that you can compare them with new ones

>[!info] Pluggable Authentication Modules (PAM)
> allows system admins to choose how applications authenticate users

for more info, you can check out the [🔗Securing Debian Manual (by Debian)](https://www.debian.org/doc/manuals/securing-debian-manual/ch04s11.en.html)
the config is set in the file `/etc/pam.d/common-password`, so open it with whatever editor you want. it contains the rules to apply to passwords

you have to change this line
```sh
password    requisite    pam_pwquality.so retry=3
```

to:

```sh
password    requisite    pam_pwquality.so retry=3 minlen=10 ucredit=-1 lcredit=-1 dcredit=-1 maxrepeat=3 reject_username difok=7 user!=root enforce_for_root
```
save and reboot! `sudo reboot`

summary:

|                    | explanation                                                                            |
| ------------------ | -------------------------------------------------------------------------------------- |
| `retry=3`          | allow for 3 retries to pass new password during password change                        |
| `minlen=10`        | minimum length of password must be 10 chars                                            |
| `ucredit=-1`       | minimum number of uppercase letters in password is 1                                   |
| `lcredit=-1`       | minimum number of lowercase letters in password is 1                                   |
| `dcredit=-1`       | minimum number of digits in password is 1                                              |
| `maxrepeat=3`      | password must not contain more than 3 consecutively repeated chars                     |
| `reject_username`  | password can't contain username                                                        |
| `difok=7`          | number of characters in new password that can't be present from the last password is 7 |
| `enforce_for_root` | apply the same rules to the `root` user                                                |
[🔗source](https://linux.die.net/man/8/pam_cracklib#:~:text=ucredit%3DN,for%20minlen%20less%20than%2010.)

>[!note] for `ucredit`, `dcredit`, `lcredit`, *minimum* amount of chars is indicated with `-`, while *maximum* amount of the chars is indicated with `+`
>

>[!warning] 
>the requirements we've put in place are only for new passwords, so we need to check the passwords we have in place already, i.e. for `root` and the `<username>` 

- update old login password to comply with the new password policy
```sh
passwd
```
![Pasted image 20250202161140.png](/img/user/Pasted%20image%2020250202161140.png)
`XXXXX` pero en el teclado nuestro. Se escribe ? pulsando la de Shift + "\_"
- check the password age of `root` and login user:
```sh
sudo chage -l facosta
```

>[!info] `chage` 
>is the command "*change age*". it's used to manipulate the time btwn password changes and the date that a password was last changed

- you need to apply the new time limits to this password as well, so do that like this:
```sh
sudo chage -M 30 -m 2 -W 7 facosta
```

all good now :)
![Pasted image 20250202162842.png](/img/user/Pasted%20image%2020250202162842.png)

and now, repeat for `root`

```sh
sudo passwd root
```
🔑 `XXX`

```sh
sudo chage -M 30 -m 2 -W 7 root
```

## new user and groups

I created the user `new_user` with the same root password `XXX`
```sh
sudo adduser new_user
```
and a new group
```sh
sudo addgroup user42
```
and add the login user to the `user42` group

```sh
sudo adduser facosta user42
```

and we can check that the user is in the group by running:
```sh
getent group user42
```

## monitoring with cron

create the script file
```sh
sudo touch /usr/local/bin/monitoring.sh
```

and give *read* and *execute* access to everyone, but *write* to owner only
```sh
sudo chmod 755 /usr/local/bin/monitoring.sh
```

and now, let's just edit the script:

>[!question] why put the script in `/usr/local/bin/monitoring.sh`?
>- `/usr/local/bin` is for programs intended to be used by everyone on this local system, and only administrator shall be able to add or remove programs from this directory
>- `/usr/local/sbin` is for program intended to be used only by local system administrators, and only administrators shall be able to add or remove programs from this directory

# monitoring script
### architecture
```sh
uname -a
```
### number of physical cores 
```sh
grep "physical id" /proc/cpuinfo | sort -u | wc -l
```
`/proc/cpuinfo` is a file that contains info about the type of processor used by your system
Each core is identified by ID "physical id" so we need to count how many times each ID appears, *uniquely* 
[🔗more about how to understand `/proc/cpuinfo`](https://doc.callmematthi.eu/static/webArticles/Understanding%20Linux%20_proc_cpuinfo.pdf)
### number of virtual cores
```sh
grep "^processor" /proc/cpuinfo | wc -l
```
>[!warning] 
>pass the regex pattern `"^"` to make sure we only count the lines that **start** with the word "processor"
### RAM
let's use the command `free` to see current info about the RAM, in *Megabytes*.
let's parse the results of running
```sh
free --mega
# free -m
```
![Pasted image 20250202190538.png](/img/user/Pasted%20image%2020250202190538.png)

using the `awk` cmd.
this
```sh
free --mega | awk '$1 == "Mem:" {print $2}'
```
means:
> for each line of the output of `free --mega`, if the first column of the line is the string `"Mem:"` => print on terminal the value of the 2nd column

and so on :)
```sh
ram_total=$(free --mega | awk '$1 == "Mem:" {print $2}')
ram_use=$(free --mega | awk '$1 == "Mem:" {print $3}')
ram_percent=$(free --mega | awk '$1 == "Mem:" {printf("%.2f"), $3/$2*100}')
```
- total RAM 
- used RAM
- percentage of used RAM with 2 decimals
### disk memory
let's use the `df` (disk file-system) command, used to get a complete summary of the use of disk space. Again we use the `-m` flag to grab the info in Megabytes

```sh
disk_total=$(df -m | grep "^/dev/" | grep -v "/boot$" | awk '{disk_t += $2} END {printf ("%.1fGb\n"), disk_t/1024}')
disk_use=$(df -m | grep "^/dev/" | grep -v "/boot$" | awk '{disk_u += $3} END {print disk_u}')
disk_percent=$(df -m | grep "^/dev/" | grep -v "/boot$" | awk '{disk_u += $3} {disk_t+= $2} END {printf("%d"), disk_u/disk_t*100}')
```

### CPU load percentage
We will use the `vmstat` command (Virtual Memory Statistics), that displays stats about system performance in real time, so we pass 1 and 2 to let it run for just 2 seconds and then, grab just the latest record with `tail -n 1`

```sh
vmstat 1 2 | tail -n 1 | awk '{cpu_usage = $13 + $14; printf "%.1f\n", cpu_usage}')

# LAST BOOT
lb=$(who -b | awk '$1 == "system" {print $3 " " $4}')

# LVM USE
lvmu=$(if [ $(lsblk | grep "lvm" | wc -l) -gt 0 ]; then echo yes; else echo no; fi)

# TCP CONNEXIONS
tcpc=$(ss -ta | grep ESTAB | wc -l)

# USER LOG
ulog=$(users | wc -w)

# NETWORK
ip=$(hostname -I | awk '{print $1}')
mac=$(ip link | grep "link/ether" | awk '{print $2}')

# SUDO
cmnd=$(journalctl _COMM=sudo | grep COMMAND | wc -l)

wall "	Architecture: $arch
	CPU physical: $cpuf
	vCPU: $cpuv
	Memory Usage: $ram_use/${ram_total}MB ($ram_percent%)
	Disk Usage: $disk_use/${disk_total} ($disk_percent%)
	CPU load: $cpu_fin%
	Last boot: $lb
	LVM use: $lvmu
	Connections TCP: $tcpc ESTABLISHED
	User log: $ulog
	Network: IP $ip ($mac)
	Sudo: $cmnd cmd"

```

### set up with CRON
Allow the script to be run without a password by going again to the sudo config:
```sh
sudo visudo
```

and add this line:
```sh
<your-user> ALL=(ALL) NOPASSWD: /usr/local/bin/monitoring.sh
```
ending up like this:
![Pasted image 20250202205652.png](/img/user/Pasted%20image%2020250202205652.png)

#### enable cron
```sh
sudo systemctl enable cron.service
```
and reboot

>[!tip]
> you may check the status of crontab at any time with a very similar command:
> ```sh
> sudo systemctl status cron.service
> ```

### edit the cron file configuration

>[!definition] `crontab`
> a Linux tool used to manage scheduled tasks (called *cron jobs*) by a user.
> in particular, *cron jobs* allow a user to execute commands or scripts automatically in specific intervals, e.g., every day, every hour, every 10min...etc.

- there is a `cron` configuration file for every user => when you want to edit a config, you must indicate the user, with the `-u` flag
- `-e` is used to indicate we want to edit the `cron` file, with the default editor

```sh
sudo crontab -u root -e
```

>[!note] 
>we are editing the `root` `cron` file so that the script is run with superuser privileges, e.g. maintaining tasks or monitoring, just what we're trying to do here :)

we will add the last line here at the end of the file:

```sh
*/10 * * * * /usr/local/bin/monitoring.sh
```
![Pasted image 20250203205618.png](/img/user/Pasted%20image%2020250203205618.png)

>[!tip] check out the screenshot for description of what the "\*" mean! ⬆

>[!tip] check what is running in a crontab 
>you can always check running processes with the command `crontab -l`.
>note that it depends, which user you're logged on. e.g., for this case, I must first log to `root` e.g., with `su -` and then run `crontab -l`

