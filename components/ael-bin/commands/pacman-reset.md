<!--
=============================================================================== 
INFO
===============================================================================
 [/ael-documentation/components/ael-bin/commands/pacman-reset.md]

 Author      : Pascal Malouin (https://github.com/alterEGO-Linux)
 Created     : 2026-09-17 11:15:45 UTC
 Updated     : 2026-09-17 11:15:45 UTC
 Description : pacman-reset.
-------------------------------------------------------------------------------
-->

# pacman-reset

Re-initializes the Arch Linux Pacman environment by rebuilding its synchronization data, refreshing the mirror list, and updating the Arch Linux keyring.

The script:

* Removes pacman's local sync database.
* Uses `reflector` to generate a fresh Canadian HTTPS mirror list from recently synchronized mirrors, sorted by download rate.
* Forces a pacman database refresh.
* Updates the `archlinux-keyring` package.

Useful for troubleshooting Pacman synchronization, outdated mirrors, or package-signing/keyring issues.

## Requirements

* AEL//Bash library (`~/.ael/lib/bash/`).
* `pacman`
* `reflector`
* `sudo`

## To Do List

* Make AEL//Bash library path flexible and configurable.
