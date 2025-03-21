# `which`, `whereis`, and `type`

## `which`
- Shows the path of the command that would run
- Example: `which ls` → `/bin/ls`

## `whereis`
- Shows locations of the binary, source, and man pages
- Example: `whereis ls` → `ls: /bin/ls /usr/share/man/man1/ls.1.gz`

## `type`
- Tells you what kind of command it is (alias, shell built-in, function, binary, etc.)
- Example: `type ls` → `ls is aliased to 'ls --color=auto'`

### Summary:
| Command   | What it shows                     |
|-----------|-----------------------------------|
| `which`   | Path to the binary in $PATH       |
| `whereis` | Binary, source, and man page path |
| `type`    | How the shell resolves the command|

