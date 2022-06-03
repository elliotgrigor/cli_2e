# Expansion

Using wildcards to make broad selections of similarly named entities.

## Path Expansion

**Shell**
```bash
user@host:~$ echo *   # expands to all VISIBLE files/directories
Desktop Documents Downloads Music Pictures Public Templates Videos
```

```bash
user@host:~$ echo .*   # expands to all HIDDEN files/directories
. .. .bash_logout .bashrc .cache .config .gitconfig .local .profile .ssh
.viminfo .vimrc
```

To omit the `.` and `..` directories, use `.[!.]`*

```bash
user@host:~$ echo .[!.]*
.bash_logout .bashrc .cache .config .gitconfig .local .profile .ssh
.viminfo .vimrc
```

## Tilde Expansion

**Shell**
```bash
user@host:~$ echo ~   # expands to the current user's home directory
/home/user
```

To list other user's home directories, append their username.

```bash
user@host:~$ echo ~john   # if user "john" exists, expands to their home directory
/home/john
```
