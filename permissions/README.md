# Permissions

Allowing and/or denying access to resources for **u**sers, **g**roups,
and **o**thers.

## User Definitions

All user accounts are defined in the `/etc/passwd` file, displaying
their ids (UID & GID), home directory, and login shell.

```bash
user@host:~$ cat /etc/passwd
```
```bash
root:x:0:0:root:/root:/bin/ash
bin:x:1:1:bin:/bin:/sbin/nologin
daemon:x:2:2:daemon:/sbin:/sbin/nologin
adm:x:3:4:adm:/var/adm:/sbin/nologin
#...
elliot:x:1000:1000:elliot:/home/elliot:/bin/bash
```

## Group Definitions

Groups are defined in the `/etc/group` file, listing their name, id, and
members.

```bash
user@host:~$ cat /etc/group
```
```bash
root:x:0:root
bin:x:1:root,bin,daemon
daemon:x:2:root,bin,daemon
sys:x:3:root,bin,adm
#...
elliot:x:1000:
```
