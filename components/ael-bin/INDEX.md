<!--
=============================================================================== 
INFO
===============================================================================
 [/ael-documentation/components/ael-bin/index.md]

 Author      : Pascal Malouin (https://github.com/alterEGO-Linux)
 Created     : 2026-09-15 14:16:43 UTC
 Updated     : 2026-09-22 20:29:46 UTC
 Description : Components: AEL//Bin.
-------------------------------------------------------------------------------
-->

# AEL//Bin

AEL//Bin is a collection of small command-line utilities and applications part 
of AlterEGO Linux.

## Installation

In an AEL ecosystem, AEL//Bin utilities and applications are installed in 
`${AEL_HOME}/bin/`.

Outside this ecosystem, we recommand installing in `~/.local/bin/`.

## List of utilities and applications.

|||
| :---------------- | :--------------------------|
|[arch-pkg](commands/arch-pkg.md)|Arch Linux package utils.|
|[busy](commands/busy.md)|A small terminal command that makes the screen look impressively busy.|
|[cheat](commands/cheat.md)|Provides an interactive interface to https://cheat.sh using `ael-fuzz`.|
|[deep-nmap](commands/deep-nmap.md)|Runs a comprehensive Nmap scan against a target using service detection, OS detection, default NSE scripts, and traceroute.|
|[deep-scan](commands/deep-scan.md)|Performs a fast port discovery with RustScan followed by a detailed Nmap scan of the discovered ports.|
|[delete](commands/delete.md)|Safely deletes one or more directories with an interactive confirmation before each deletion.|
|[dicom-tag](commands/dicom-tag)|Provides an interactive DICOM tag reference using `ael-fuzz`.|
|[directory-size](commands/directory-size)|Displays the size of the current directory and its largest immediate child directories.|
|[elevate](commands/elevate.md)|Repeats last command with sudo, if forgotten.|
|[emojis](commands/emojis.md)|Provides an interactive emoji picker for the terminal using `ael-fuzz`.|
|[pacman-reset](command/pacman-reset.md)|Re-initialize pacman sync, mirrorlist and keyring.|
|[processes](commands/processes.md)|Displays a detailed list of all currently running processes.|
|[ports](commands/ports.md)|Displays all listening and active TCP/UDP ports, including the processes associated with them.|
|[py-cleaner](commands/py-cleaner.md)|Cleans Python-generated cache files from the current directory and its subdirectories.|
|[shell-info](command/shell-info.md)|Inspects the current Bash environment and displays detailed information about aliases, functions, variables, builtins, and shell keywords.|
|[show-utc](commands/show-utc.md)|Show UTC time in terminal.|
|[whoisweb](commands/whoisweb.md)|Query WHOIS web if whois port 43 is blocked on your network.|
|[word-frequency](commands/word-frequency.md)|Counts word occurrences from a file or standard input and displays them by frequency or alphabetically.|

## Source

[AEL//Bin GitHub repository](https://github.com/alterEGO-Linux/ael-bin): https://github.com/alterEGO-Linux/ael-bin.
