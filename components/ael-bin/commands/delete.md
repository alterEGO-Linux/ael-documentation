<!--
=============================================================================== 
INFO
===============================================================================
 [/ael-documentation/components/ael-bin/commands/delete.md]

 Author      : Pascal Malouin (https://github.com/alterEGO-Linux)
 Created     : 2026-09-17 11:06:27 UTC
 Updated     : 2026-09-17 11:06:27 UTC
 Description : delete
-------------------------------------------------------------------------------
-->

# delete

Safely deletes one or more directories with an interactive confirmation before each deletion.

```bash
delete old-directory
delete cache tmp backup
```

Directories that do not exist are skipped with an error message. The command refuses to proceed when no interactive terminal is available, preventing accidental unattended deletion.

## Requirements

* AEL//Bash library (`~/.ael/lib/bash/`).
* `bash`

## To Do List

* Make AEL//Bash library path flexible and configurable.
