---
{"dg-publish":true,"permalink":"/☆⋆｡𖦹°‧★🛸42/⋆｡ﾟ🪐｡⋆ ﾟ☾ ﾟ⋆common-core/01/🌱born2beroot/📝eval/❓questions b2br/","tags":["42madrid","unix","milestone1"]}
---


- `signature.txt` file at the root of the repo
- signature contained in `signature.txt` must be **IDENTICAL** to the one of the `.vdi` file of the virtual machine
	- [!] should match identically under a `diff` cmd

>[!warning] remind evaluator to **duplicate machine** to avoid possible issues


# overview
>[!question]  qué es una máquina virtual?
>es un software que simula una [[☆⋆｡𖦹°‧★🛸42/⋆｡ﾟ🪐｡⋆ ﾟ☾ ﾟ⋆common-core/01/🌱born2beroot/📝eval/📚notes/computing system\|computadora]] o *sistema de computación*. sus recursos (CPU, memoria, almacenamiento) son software, no físicos (hardware) y se *prestan* de recursos que sí son físicos (de la máquina o *anfitrión* desde el que corren)
>🔗[[☆⋆｡𖦹°‧★🛸42/⋆｡ﾟ🪐｡⋆ ﾟ☾ ﾟ⋆common-core/01/🌱born2beroot/📝eval/📚notes/virtual machine\|virtual machine]]

te permiten un entorno nuevo aislado de tu máquina. esto tiene varios usos:
- backing up an existing OS
- specially, images, are used to easily move or run the same machine on different machines, e.g. if you have different laptops you can just carry your image in a pendrive and "mostly" not care about the physical machine you're working on
- offering an already set up environment for, e.g. devs
- trying out software you're not sure about, on a specific environment
- try out (possibly) unsafe software


>[!question] por qué *Debian* y no *Rocky*?
> porque incluso en el *subject* indica que manejarlo es más sencillo y porque es con el que tengo más costumbre por mi trabajo

>[!question] diferencias Debian vs Rocky


|                                         | debian           | rocky                       |
| --------------------------------------- | ---------------- | --------------------------- |
| base                                    | independiente    | RHEL                        |
| [[☆⋆｡𖦹°‧★🛸42/⋆｡ﾟ🪐｡⋆ ﾟ☾ ﾟ⋆common-core/01/🌱born2beroot/📝eval/📚notes/package manager\|gestor de paquetes]] | APT (.deb)       | DNF (.rpm)                  |
| estabilidad                             | más flexible \*  | muy estable(p. empresas...) |
| soporte                                 | 3-5 años         | 10 años                     |
| uso típico                              | genérico, amplio | comercial                   |

>[!summary]
> debian más versátil, desarrollo comunitario
> rocky más robusto, perfecto para llevar a producción y soporte a largo plazo

- **base**: 
	- *debian*: independiente, i.e. no respaldada por organizaciones, compañías, etc., si no por una comunidad
	- *rocky*: es una alternativa desarrollada por una comunidad y gratuita a **RHEL** (Red Hat Enterprise Linux)
		- es un Linux commercial con licencia de código abierto (i.e. público) desarrollado por la compañía **Red Hat**, sobre todo para el *mercado comercial*
			- **Red Hat** comprada x IBM en 2018

- ciclo de lanzamiento("*release cycle*") más rápido y frecuente en Rocky > Debian
	- [i] en relación a *estabilidad*, de hecho, en Debian te sueles encontrar que las versiones más nuevas de paquetes, software etc. suelen estar en las versiones *Unstable*, i.e. más nuevas que la última *Stable*

## preguntas para Debian
>[!question] *apt* vs *aptitude*
> *apt* es el resultado de reescribir `apt-get` un antiguo gestor de paquetes de Debian por dar outputs más unificados, más estandarizado, moderno, etc. se supone que es el reemplazo de `apt-get`, aunque se sigue pudiendo usar ambos
> *aptitude* es una interfaz de texto(en terminal) lanzada como alternativa (1999) a `apt-get`. aunque tiene diferencias por debajo, a efectos prácticos hace lo mismo que `apt/apt-get` pero en interfaz

⬇ capturas de aptitude (oficiales, [🔗source](https://screenshots.debian.net/package/aptitude))
![large-8ddba4b287ad8b82f4df8aad6eb8a0b1.png](/img/user/large-8ddba4b287ad8b82f4df8aad6eb8a0b1.png)
![large-bcc489d55704c7b1eff3ffb821efdce1.png](/img/user/large-bcc489d55704c7b1eff3ffb821efdce1.png)


>[!question] qué es AppArmor?
> "Application Armor" es un módulo de seguridad del kernel de Linux que permite al administrador del sistema editar/restringir las capacidades de un programa

- [i] hoy en día mantenido por *Canonical* (los que llevan Ubuntu, una distro basada en Debian) desde 2009
Es una alternativa a **SELinux**, al parecer diseñada para ser *más fácil de instalar y mantener*.

>[!note] tiene que estar el script corriendo y printeando cosas cada 10min, pero se verá en detalle más adelante


# comandos para la eval

## simple setup

### revisar que no hay una interfaz gráfica en uso

```sh
ls /usr/bin/*session
```

>[!success] algo como esto
> ```sh
> /usr/bin/dbus-run-session
> ```

>[!failure]
>e.g. GNOME (la de x defecto en, e.g., Ubuntu)
>```sh
>/usr/bin/dbus-run-session  /usr/bin/gnome-session-custom-session
/usr/bin/gnome-session
>```


### revisar que el servicio de UFW está en uso

siempre puedes chequear qué tal está el [[☆⋆｡𖦹°‧★🛸42/⋆｡ﾟ🪐｡⋆ ﾟ☾ ﾟ⋆common-core/01/🌱born2beroot/📝eval/📚notes/UFW\|UFW]] con:
```sh
sudo ufw status
```

>[!success]
>tiene que mostrar algún texto diciendo "active", e.g.:
> ![Pasted image 20250123192425.png](/img/user/Pasted%20image%2020250123192425.png)

también conviene que chequees el propio estado del *servicio* de UFW:

```sh
sudo service ufw status
```

que se ocupa de verificar si el UFW está habilitado o no. 

>[!success]
> idem, algo que diga "active"
> ![Pasted image 20250123192336.png](/img/user/Pasted%20image%2020250123192336.png)

#### diferencia

`service ufw status` te indica si el propio *daemon* de `ufw` está habilitado, i.e. preparado para hacer cosas
`ufw status` te indica *qué* está haciendo el *daemon*, i.e. si está haciendo cosas ("*active*") o no

> - Service: Active, UFW: Active: I'm here and I'm doing my job.
> - Service: Active, UFW: Inactive: I'm here and I'm doing nothing.

🔗[source: `ufw status` vs `service ufw status`](https://askubuntu.com/questions/923734/ufw-status-vs-service-ufw-status)


### revisar que el servicio de SSH está en uso

para revisar el ssh:
```sh
sudo service ssh status
```

>[!success]
>algo que diga "*active*"
>![Pasted image 20250123193809.png](/img/user/Pasted%20image%2020250123193809.png)


>[!tip] si quieres ver más cosas...(no estoy muy segura de esto...)
>```sh
> sudo service ssh restart; tail -f /var/log/syslog
>```

> If the `ssh` service is **not OK** then you'll see something like this with exit codes, status etc:
> 
>```sh
>Jun  2 10:57:03 xfce systemd[1]: ssh.service: main process exited, code=exited, status=255/n/a
>Jun  2 10:57:03 xfce systemd[1]: Unit ssh.service entered failed state.
>Jun  2 10:57:03 xfce systemd[1]: ssh.service failed.
>Jun  2 10:57:03 xfce systemd[1]: ssh.service holdoff time over, scheduling restart.
>Jun  2 10:57:03 xfce systemd[1]: start request repeated too quickly for ssh.service
>Jun  2 10:57:03 xfce systemd[1]: Failed to start OpenBSD Secure Shell server.
>```
>
>But if it **is OK** then:
>
>```sh
Jun  2 10:57:31 xfce systemd[1]: Started OpenBSD Secure Shell server.
Jun  2 10:57:31 xfce systemd[1]: Starting OpenBSD Secure Shell server...
>```
[🔗source](https://superuser.com/questions/923107/ssh-service-status)


### revisar que utilizas el SO Debian o CentOS

```sh
uname -v
```

o

```sh
uname --kernel-version
```

y aparecerá "Debian" en el resultado

>[!info] "uname" means *unix name*

## User stuff

### revisar que tu usuario está dentro de los grupos "sudo" & "user42"

con el comando "`getent`" (*get entries*) que te extrae entradas de una serie de archivos de texto muy importante "bases de datos" soportadas por la librería [[🖥/🛠/🕸networks/name service switch (NSS) library\|NSS]] 
```sh
getent ...
```

Le pasamos la opción `group` para acceder a la base de datos `group` y luego, el grupo cuyos usuarios queremos revisar, e.g.

```sh
getent group sudo
```

```sh
getent group user42
```

y revisamos que salga (al menos) 1 registro con el nombre de nuestro usuario

>[!example]
> esto significa que el usuario "bocal" está en el grupo sudo
>![Pasted image 20250201141106.png](/img/user/Pasted%20image%2020250201141106.png)


### crea un nuevo usuario y muestra que sigue la política de contraseñas del subject

para crear un usuario, lo hacemos con el comando `adduser`

```sh
sudo adduser name_user
```

la configuración se hace en varios sitios:

algunos tiempos se configuran en el archivo `/etc/login.defs`(puedes abrirlo con nano) y baja un buen rato

- password expires in 30 days with a 2-day minimum change limit and a 7-day warning

para revisar el resto de políticas de seguridad, ve a [[☆⋆｡𖦹°‧★🛸42/⋆｡ﾟ🪐｡⋆ ﾟ☾ ﾟ⋆common-core/01/🌱born2beroot/🔨job/🏗work b2br#password policy\|🏗work b2br#password policy]]

el otro archivo donde se configura la política de contraseñas es en `/etc/pam.d/common-password`

cuando te pida una contraseña, si sigue todas las reglas, saldrá todo bien 

>[!example]
>![Pasted image 20250201141258.png](/img/user/Pasted%20image%2020250201141258.png)

### crear un nuevo grupo "*evaluating*"

similarmente, usamos el comando `addgroup`

```sh
sudo addgroup evaluating
```

### añadir el usuario nuevo al nuevo grupo

```sh
sudo adduser name_user evaluating
```


>[!tip] por si acaso
> puedes revisar que el grupo se ha creado correctamente con `getent`
> ```sh
> getent group evaluating
> ```


## hostname stuff & partitions
### comprobar que el hostname de la máquina es correcto

i.e., el login de 42 del evaluado (yo)

```sh
hostname
```

>[!success]
> e.g.,
>![Pasted image 20250201142249.png](/img/user/Pasted%20image%2020250201142249.png)

>[!info] hostname
> el nombre dado a la máquina, usado para identificarla únicamente en una red
>

### modificar hostname por el login delx evaluadorx
e.g., `student42`

el *hostname* de una máquina se edita editando el archivo `/etc/hostname`, e.g., con `nano`
```sh
sudo nano /etc/hostname
```
>[!definition] archivo `hostname`
> se ocupa de contener el nombre de la máquina

simplemente cambia la 1a línea por `student42`

también hay que editar el archivo de "*hosts*"
```sh
sudo nano /etc/hosts
```
>[!example]
> ![Pasted image 20250201144509.png](/img/user/Pasted%20image%2020250201144509.png)


>[!definition] archivo `hosts`
> contiene los host names (del protocolo de Internet(IP)) y las direcciones (IPs) para el local hosts y otros hosts en la red de internet
> - [i] se usa para resolver(traducir) un nombre a una dirección (un hostname a una dcción de Internet)

Para que los cambios surjan efecto, hace falta reiniciar la máquina
```sh
sudo reboot
```
tras lo cual podemos ver cómo el *hostname* ha cambiado, e.g., ejecutando el comando `hostname`


### comprobar que las particiones son tal y cómo describe el subject 

podemos revisar el estado de las particiones con el comando [[🖥/🛠/🕸networks/lsblk\|lsblk]]
y comprobar que sea igual que en el subject:
![Pasted image 20250201150715.png](/img/user/Pasted%20image%2020250201150715.png)


#todo learn LVM and what is it, etc. 
>[!definition] LVM
> un gestor de volúmenes lógicos. abstrae el concepto de particiones "físicas" y te permite manejar volúmenes de forma más flexible. E.g., abarcando varias particiones a la vez en un mismo volumen.

para más info puedes mirar [[🖥/🛠/🕸networks/logical volumes vs logical partitions\|logical volumes vs logical partitions]]


## sudo

>[!definition] sudo (superuser do)
> es un programa de Linux que permite a usuarios correr programas con los privilegios de seguridad de otros usuarios (sin necesidad de cambiar de login)

permite a usuarios "normales", que estén agregados al grupo de administradores (`sudo`) poder acceder a los privilegios de administrador que pueda necesitar
### comprobar que sudo está instalado

```sh
dpkg -s sudo
```
es mejor que `which` porque al parecer which no siempre busca en todas las carpetas que te interesa para encontrar programas instalados

### añadir nuevo usuario al grupo sudo 
```sh
sudo adduser new_user sudo
```
y para comprobar que se ha añadido correctamente
```sh
getent group sudo
```

### mostrar las reglas aplicadas a sudo por el subject

```sh
sudo visudo
```

- [i] **NOTE** `requiretty` is to enforce TTY("teletype writer") for usage of sudo. This means to require being logged-in terminal session to be able to use sudo. This avoids sudo being used from some? automated processes daemons, cronjobs, etc.

### comprueba que la ruta `/var/log/sudo` existe y hay al menos 1 archivo conteniendo logs de entrada y salida
```sh
ls /var/log/sudo
```

check the logs to contain I/O from sudo:
```sh
tail /var/log/sudo
```

## UFW / Firewalld

### comprobar que UFW está instalado
```sh
dpkg -s ufw
```

### comprobar que funciona correctamente

```sh
sudo service ufw status
```

### lista las reglas de UFW

```sh
sudo ufw status numbered
```

y comprueba que solo debe aparecer la regla para el puerto 4242

### añade una regla para el puerto 8080
```sh
sudo ufw allow 8080
```

y comprueba otra vez con `sudo ufw status numbered`

### borra regla
e.g.,
```sh
sudo ufw delete num_rule(id)
```

## SSH 

### comprobar que SSH está instalado
```sh
which ssh
```

### comprobar estado de SSH, que esté corrien2
```sh
sudo service ssh status
```

### usa SSH para iniciar sesion con el usuario recien creado
y asegúrate de que no se puede entrar con `root`

## cron

### modifica el tiempo de ejecución del script de 10 a 1 minutos
```sh
sudo crontab -u root -e
```

recuerda que tienes que pasas el flag de usuario porque estás editando el cron file de root, que es quien esta a cargo de ejecutar el script

### haz que el script deje de ejecutarse cuando el servidor se haya iniciado, pero sin modificar el script
```sh
sudo /etc/init.d/cron stop
```


```sh
sudo service cron stop
sudo systemctl disable cron
sudo systemctl is-enabled cron # para revisar
```
### y para volver a encenderlo
```sh
sudo /etc/init.d/cron start
```

