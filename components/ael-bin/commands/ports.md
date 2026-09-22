<!--
=============================================================================== 
INFO
===============================================================================
 [/ael-documentation/components/ael-bin/commands/ports.md]

 Author      : Pascal Malouin (https://github.com/alterEGO-Linux)
 Created     : 2026-09-21 11:17:48 UTC
 Updated     : 2026-09-21 11:17:48 UTC
 Description : ports.
-------------------------------------------------------------------------------
-->

# ports

Displays all listening and active TCP/UDP ports, including the processes associated with them.

```bash
ports
```

Uses `netstat` with elevated privileges to show addresses, ports, connection states, PIDs, and process names. If `grc` is available, the output is automatically colorized.

## Requirements

* AEL//Bash library (`~/.ael/lib/bash/`).
* `grc`
* `netstat`
* `sudo`

## To Do List

* Make AEL//Bash library path flexible and configurable.
