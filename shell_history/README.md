# Shell History

Making use of the `.bash_history` file.

## The `history` command

Previously executed commands can be viewed and searched for using `history`.

`history` on its own displays all the previous commands run, up to a specified limit.

**Input**
```bash
user@host:~$ history
```

**Output**
```bash
  # etc...
  241  cd sf/cli_2e/
  242  la
  243  mkdir shell_history
  244  cd shell_history/
  245  touch README.md
  246  history
```

## Expansion with `history`

If, for example, a specific history entry was searched for, expansion
could be performed using the line number associated with the historical
command.

**Example**
```bash
user@host:~$ history | grep js_dsa
  109  cd ~/sf/js_dsa
```

The `!` command can be used to run historical commands if you have
access to the `.bash_history` file's line number.

```bash
user@host:~$ !109
user@host:~/sf/js_dsa$
```
