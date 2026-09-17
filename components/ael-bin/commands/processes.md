<!--
=============================================================================== 
INFO
===============================================================================
[/ael-documentation/components/ael-bin/commands/processes.md]

Author      : Pascal Malouin (https://github.com/alterEGO-Linux)
Created     : 2026-09-15 21:12:00 UTC
Updated     : 2026-09-15 21:12:00 UTC
Description : processes.
-------------------------------------------------------------------------------
-->

# processes

Displays a detailed list of all currently running processes.

```bash
processes
```

Shows process ownership, CPU and memory usage, state, start time, and command information using `ps aux`. If `grc` is available, the output is automatically colorized.

## Requirements

* AEL//Bash library (`~/.ael/lib/bash/`).
* `grc` (optional)
* `ps`

## To Do List

* Make AEL//Bash library path flexible and configurable.
