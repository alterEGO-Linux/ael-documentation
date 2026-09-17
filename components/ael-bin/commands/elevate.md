<!--
=============================================================================== 
INFO
===============================================================================
 [/ael-documentation/components/ael-bin/commands/elevate.md]

 Author      : Pascal Malouin (https://github.com/alterEGO-Linux)
 Created     : 2026-09-17 10:48:17 UTC
 Updated     : 2026-09-17 10:48:17 UTC
 Description : elevate.
-------------------------------------------------------------------------------
-->

# elevate

Repeats the previous shell command with elevated privileges using `sudo`.

```bash
pacman -Syu
# error: you cannot perform this operation unless you are root.

elevate
```

An optional interactive mode asks for confirmation before executing the command:

```bash
elevate --interactive
```

Because `elevate` relies on Bash command history, the script must be **sourced** rather than executed directly.

## Requirements

* AEL//Bash library (`~/.ael/lib/bash/`).
* `bash`
* `sudo`

## To Do List

* Make AEL//Bash library path flexible and configurable.
