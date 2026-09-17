<!--
=============================================================================== 
INFO
===============================================================================
 [/ael-documentation/components/ael-bin/commands/deep-scan.md]

 Author      : Pascal Malouin (https://github.com/alterEGO-Linux)
 Created     : 2026-09-17 02:04:22 UTC
 Updated     : 2026-09-17 02:04:22 UTC
 Description : deep-scan
-------------------------------------------------------------------------------
-->

# deep-scan

Performs a fast port discovery with RustScan followed by a detailed Nmap scan of the discovered ports.

```bash
deep-scan 192.168.1.1
deep-scan localhost
```

Nmap performs service and OS detection, runs its default scripts, and includes a traceroute. If `grc` is available, the Nmap output is automatically colorized.

## Requirements

* AEL//Bash library (`~/.ael/lib/bash/`).
* `grc` (optional)
* `nmap`
* `rustscan`
* `sudo`

## To Do List

* Make AEL//Bash library path flexible and configurable.
