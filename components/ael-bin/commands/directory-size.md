<!--
=============================================================================== 
INFO
===============================================================================
 [/ael-documentation/components/ael-bin/commands/directory-size.md]

 Author      : Pascal Malouin (https://github.com/alterEGO-Linux)
 Created     : 2026-09-21 11:32:01 UTC
 Updated     : 2026-09-21 11:32:01 UTC
 Description : directory-size
-------------------------------------------------------------------------------
-->

# directory-size

Displays the size of the current directory and its largest immediate child directories.

```bash
directory-size
```

Results are sorted from largest to smallest and shown in human-readable units, making it easy to quickly identify directories consuming the most disk space.

## Requirements

* AEL//Bash library (`~/.ael/lib/bash/`).
* `du`
* `head`
* `sort`

## To Do List

* Make AEL//Bash library path flexible and configurable.
