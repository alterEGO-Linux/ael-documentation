<!--
=============================================================================== 
INFO
===============================================================================
[/ael-documentation/components/ael-bin/commands/cheat.md]

Author      : Pascal Malouin (https://github.com/alterEGO-Linux)
Created     : 2026-09-22 20:03:36 UTC
Updated     : 2026-09-22 20:03:36 UTC
Description : cheat.
-------------------------------------------------------------------------------
-->

### cheat

Provides an interactive interface to [cheat.sh](https://cheat.sh) using `ael-fuzz`.

```bash
cheat
```

Browse and search available cheat sheets with a live preview, then open the selected reference in `less`. The preview automatically adapts to the terminal size.

## Requirements

* AEL//Bash library (`~/.ael/lib/bash/`).
* `ael-fuzz`
* `curl`
* `less`

## To Do List

* Make AEL//Bash library path flexible and configurable.

## Resources

* [Cheat.sh on GitHub](https://github.com/chubin/cheat.sh)
