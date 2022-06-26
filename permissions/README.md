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

## Changing the File Mode

Using the `chmod` command to alter user, group, and world access to files.

### Octal Representation

Octal maps nicely to each combination of permissions. Combining three of
the following will respectively set the file permissions for the user,
group, and world.

| Octal | Binary | File mode |
|-------|--------|-----------|
| 0 | 000 | `---` |
| 1 | 001 | `--x` |
| 2 | 010 | `-w-` |
| 3 | 011 | `-wx` |
| 4 | 100 | `r--` |
| 5 | 101 | `r-x` |
| 6 | 110 | `rw-` |
| 7 | 111 | `rwx` |

```bash
-rw-rw-r-- 1 user user 0 Jun 26 12:41 file1.txt
```
```bash
user@host:~$ chmod 640 file1.txt
```
```bash
-rw-r----- 1 user user 0 Jun 26 12:41 file1.txt
```

### Symbolic Representation

Symbols are a more human-readable way of visualising file permissions
before applying the changes. This is achieved by mapping each symbol to
a set of permissions <small>(any combination of `r`, `w`, `x`)</small>.

| Character | Meaning |
|-----------|---------|
| <small>**Affected**<small> |  |
| `u` | User <sup>(owner)<sup> |
| `g` | Group |
| `o` | Other <sup>(world)</sup> |
| `a` | All <sup>(combining `u`, `g`, and `o`)</sup> |
| <small>**Operator**<small> |  |
| `=` | Set <sup>(override)<sup> |
| `+` | Append |
| `-` | Remove |
| <small>**Permission**<small> |  |
| `r` | Read |
| `w` | Write |
| `x` | Execute <sup>(all)</sup> |
| `X` | Execute <sup>(only directories)</sup> |

```bash
-rw-rw-r-- 1 user user 0 Jun 26 12:41 file1.txt
```
```bash
user@host:~$ chmod u=rwx,g-w+x,o-rwx file1.txt
```
```bash
-rwxr-x--- 1 user user 0 Jun 26 12:41 file1.txt
```
