
# Redirection

Using the output from a command elsewhere instead of printing it to the
terminal.

## Redirecting standard output *(stdout)*

**Write**
```bash
user@host:~$ ls -lh /bin/ > out.txt
```

**Append**

```bash
user@host:~$ ls -lh /bin/ >> out.txt
```

## Redirecting standard error *(stderr)*

**Write**
```bash
user@host:~$ ls -lh ~/doesnotexist/ 2> err.txt
```

**Append**
```bash
user@host:~$ ls -lh ~/doesnotexist/ 2>> err.txt
```

## Combined *stdout* and *stderr* redirection

**Input**

```bash
user@host:~$ ls -lh /bin/ >> out.txt 2>> err.txt
user@host:~$ ls -lh ~/doesnotexist/ >> out.txt 2>> err.txt
```

**Output**

```bash
-rw-r-----. 1 user user  74 Jun  1 18:10 err.txt
-rw-r-----. 1 user user 56K Jun  1 18:10 out.txt
```

```
### err.txt ###
ls: cannot access '/home/user/doesnotexist/': No such file or directory
```

```
### out.txt ###
total 111M
-rwxr-xr-x. 1 root root      53K Mar 21 08:15 [
-rwxr-xr-x. 1 root root     1.3K May 24  2021 abrt
-rwxr-xr-x. 1 root root      16K Oct  5  2021 abrt-action-analyze-backtrace
-rwxr-xr-x. 1 root root      20K Oct  5  2021 abrt-action-analyze-c
-rwxr-xr-x. 1 root root     1.3K Oct  5  2021 abrt-action-analyze-ccpp-local
-rwxr-xr-x. 1 root root     4.6K Oct  5  2021 abrt-action-analyze-core
-rwxr-xr-x. 1 root root      16K Oct  5  2021 abrt-action-analyze-oops
-rwxr-xr-x. 1 root root      16K Oct  5  2021 abrt-action-analyze-python
-rwxr-xr-x. 1 root root     2.6K Oct  5  2021 abrt-action-analyze-vmcore
...
```

**Modern method**

This operator combines both *standard output* and *standard error* and
outputs both to the same file.

```bash
user@host:~$ ls -lh /bin/ &> out.txt    # write
```

```bash
user@host:~$ ls -lh /bin/ &>> out.txt   # append
```
