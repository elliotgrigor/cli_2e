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

## Incremental Search

The shell history can be searched character by character using
incremental search with the keyboard shortcut, **Ctrl+R**.

Tip: **Ctrl+G** or **Ctrl+C** can be used to exit incremental search.

**Shell**
```bash
(reverse-i-search)`':
```

```bash
(reverse-i-search)`cd': cd ~/sf/js_dsa
#    search term --^^   ^^-- result(s)   # keep pressing Ctrl+R to search further back
```

**Return ⏎** immediately executes the selected command.
**Ctrl+J** copies the selected command to the shell prompt.
