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