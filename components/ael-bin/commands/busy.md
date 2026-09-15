<!--
=============================================================================== 
INFO
===============================================================================
[/ael-documentation/components/ael-bin/commands/busy.md]

Author      : Pascal Malouin (https://github.com/alterEGO-Linux)
Created     : 2026-09-15 15:04:42 UTC
Updated     : 2026-09-15 15:04:42 UTC
Description : busy.
-------------------------------------------------------------------------------
-->

# busy

A small terminal command that makes the screen look impressively busy.

It continuously reads random data, displays it as a hexadecimal dump, and highlights occurrences of `ca fe` until stopped with `Ctrl+C`.

```bash
busy
```

## Requirements

* AEL//Bash library (`~/.ael/lib/bash/`).
* `bash`
* `cat`
* `grep`
* `hexdump`

## To Do List

* Make AEL//Bash library path flexible and configurable.
