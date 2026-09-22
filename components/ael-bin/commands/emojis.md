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

Provides an interactive emoji picker for the terminal using `fzf`.

```bash
emojis
```

Searches a built-in emoji database containing Unicode codes and descriptions. The selected emoji is automatically copied to the clipboard using `wl-copy` under Wayland or `xclip` under X11.

**Requirements:** `fzf`, `wl-copy` (Wayland) or `xclip` (X11), and the AEL Bash library.

