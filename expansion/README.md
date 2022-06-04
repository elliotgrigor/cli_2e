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

### Selections

**Numbers**
```bash
user@host:~/split_file$ ls bigfile.part{1,3}.zip   # only 1 and 3
bigfile.part1.zip bigfile.part3.zip
```

**Letters**
```bash
user@host:~/split_file$ ls alpha{A,M,Z}.txt   # only A, M, and Z
alphaA.txt alphaM.txt alphaZ.txt
```

### Nesting

```bash
user@host:~/split_file$ ls -l bigfile.part{A{1,2,3},B{i,ii},C{01..4}}.zip
-rw-r----- 1 user user 0 Jun  4 14:31 bigfile.partA1.zip
-rw-r----- 1 user user 0 Jun  4 14:31 bigfile.partA2.zip
-rw-r----- 1 user user 0 Jun  4 14:31 bigfile.partA3.zip
-rw-r----- 1 user user 0 Jun  4 14:31 bigfile.partBi.zip
-rw-r----- 1 user user 0 Jun  4 14:31 bigfile.partBii.zip
-rw-r----- 1 user user 0 Jun  4 14:31 bigfile.partC01.zip
-rw-r----- 1 user user 0 Jun  4 14:31 bigfile.partC02.zip
-rw-r----- 1 user user 0 Jun  4 14:31 bigfile.partC03.zip
-rw-r----- 1 user user 0 Jun  4 14:31 bigfile.partC04.zip
```

In the above example, note that `01` is being used instead of `1`. This
is a feature of bash >= 4.0, and allows for the prepending of zeros.
Known as ***zero padding***.

## Parameter Expansion

Using shell variables to make selections.

```bash
user@host:~$ echo $USER; echo $HOME; echo $GOPATH
user
/home/user
/home/user/go
```

## Command Substitution

Using the output of a command as an expansion.

```bash
user@host:~$ ls -alh $(which go)
lrwxrwxrwx 1 root root 18 Jun  2 10:43 /usr/bin/go -> /usr/lib/go/bin/go
```
