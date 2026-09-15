<!--
=============================================================================== 
INFO
===============================================================================
[/ael-documentation/components/ael-bin/commands/deep-nmap.md]

Author      : Pascal Malouin (https://github.com/alterEGO-Linux)
Created     : 2026-09-15 15:21:14 UTC
Updated     : 2026-09-15 15:21:14 UTC
Description : deep-nmap.
-------------------------------------------------------------------------------
-->

# deep-nmap

Runs a comprehensive Nmap scan against a target using service detection, OS detection, default NSE scripts, and traceroute.

```bash
deep-nmap 192.168.1.1
deep-nmap scanme.nmap.org --Pn
```

Additional Nmap options can be supplied directly. If `grc` is available, the scan output is automatically colorized.

## Requirements

* AEL//Bash library (`~/.ael/lib/bash/`).
* `grc` (optional)
* `nmap`
* `sudo`

## To Do List

* Make AEL//Bash library path flexible and configurable.
