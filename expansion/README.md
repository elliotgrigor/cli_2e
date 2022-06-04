# Expansion

Using wildcards and expressions to make broad selections of similarly
named entities.

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

## Arithmetic Expansion

The `$(( ... ))` syntax can be used to expand arithmetic to be used as
standard input.

Supported operators are as follows:

| Operator | Description         |
|----------|---------------------|
| `+`      | Addition            |
| `-`      | Subtraction         |
| `*`      | Multiplication      |
| `/`      | Division            |
| `%`      | Modulo (remainder)  |
| `**`     | Exponent (power of) |

**Shell**
```bash
user@host:~$ echo $(( 5 + 5 ))
10
user@host:~$ echo $(( 25 - 9 ))
16
user@host:~$ echo $(( 16 * 4 ))
64
user@host:~$ echo $(( 107 / 7 )). Only integers are supported
15. Only integers are supported
user@host:~$ echo $(( 107 % 7 ))
2
user@host:~$ echo $(( 6 ** 9 ))
10077696
```

## Brace Expansion

Creating matches using a specified pattern within `{}` braces.

Like path expansion, selections are made based on the entities which
match the pattern within the braces.

### Ranges

**Numbers**
```bash
user@host:~/split_file$ ls bigfile.part{0..3}.zip   # 0 to 3
bigfile.part0.zip bigfile.part1.zip bigfile.part2.zip bigfile.part3.zip
```

**Letters**
```bash
user@host:~/split_file$ ls alpha{K..P}.txt   # K to P
alphaK.txt alphaL.txt alphaM.txt alphaN.txt alphaO.txt alphaP.txt
```
