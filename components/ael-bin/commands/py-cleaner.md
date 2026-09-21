<!--
=============================================================================== 
INFO
===============================================================================
 [/ael-documentation/components/ael-bin/commands/py-cleaner.md]

 Author      : Pascal Malouin (https://github.com/alterEGO-Linux)
 Created     : 2026-09-21 11:07:18 UTC
 Updated     : 2026-09-21 11:07:18 UTC
 Description : py-cleaner.
-------------------------------------------------------------------------------
-->

# py-cleaner

Cleans Python-generated cache files from the current directory and its subdirectories.

```bash
py-cleaner
```

Recursively removes `__pycache__` directories and compiled `.pyc` and `.pyo` files, providing a quick way to clean a Python project tree.

## Requirements

* AEL//Bash library (`~/.ael/lib/bash/`).
* `find`

## To Do List

* Make AEL//Bash library path flexible and configurable.
