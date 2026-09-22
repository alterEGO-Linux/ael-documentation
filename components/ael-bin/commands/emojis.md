<!--
=============================================================================== 
INFO
===============================================================================
[/ael-documentation/components/ael-bin/commands/emojis.md]

Author      : Pascal Malouin (https://github.com/alterEGO-Linux)
Created     : 2026-09-22 12:35:27 UTC
Updated     : 2026-09-22 12:35:27 UTC
Description : emojis
-------------------------------------------------------------------------------
-->

# emojis

Provides an interactive emoji picker for the terminal using `ael-fuzz`.

```bash
emojis
```

Searches a built-in emoji database containing Unicode codes and descriptions. The selected emoji is automatically copied to the clipboard using `wl-copy` under Wayland or `xclip` under X11.

The data file is created using `generate-emoji-json` which queries <https://www.unicode.org/Public/emoji/latest/emoji-test.txt>.

## Requirements

* AEL//Bash library (`~/.ael/lib/bash/`).
* `ael-fuzz`
* `wl-copy` (for Wayland)
* `xclip` (for X11)

## To Do List

* Make AEL//Bash library path flexible and configurable.
* Add a .desptop and ael-fuzz --frontend quickshell.
* Add proper font for rich display.
