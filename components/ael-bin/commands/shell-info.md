<!--
=============================================================================== 
INFO
===============================================================================
[/ael-documentation/components/ael-bin/commands/shell-info.md]

Author      : Pascal Malouin (https://github.com/alterEGO-Linux)
Created     : 2026-09-18 11:51:25 UTC
Updated     : 2026-09-18 11:51:25 UTC
Description : description
-------------------------------------------------------------------------------
-->

### shell-info

Inspects the current Bash environment and displays detailed information about aliases, functions, variables, builtins, and shell keywords.

```bash
shell-info tmuxplus
shell-info --fuzz
shell-info --sourced
shell-info --sourced-tree
```

When available, `shell-info` identifies where aliases, functions, and variables were defined. It can also interactively browse the shell environment with `ael-fuzz` or `fzf`, list files loaded during shell startup, or display them as a dependency tree.

The script must be **sourced** to inspect the current shell environment correctly.

## Requirements

* AEL//Bash library (`~/.ael/lib/bash/`).
* `bash`
* `awk`
* `grep`
* `sed`
* `tac`
* `ael-fuzz` (optional)
* `fzf` (optional)

## To Do List

* Make AEL//Bash library path flexible and configurable.
