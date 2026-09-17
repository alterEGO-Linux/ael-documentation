<!--
=============================================================================== 
INFO
===============================================================================
 [/ael-documentation/components/ael-bin/commands/arch-pkg.md]

 Author      : Pascal Malouin (https://github.com/alterEGO-Linux)
 Created     : 2026-09-15 21:01:30 UTC
 Updated     : 2026-09-15 21:01:30 UTC
 Description : arch-pkg.
-------------------------------------------------------------------------------
-->

# arch-pkg

Provides convenient command-line helpers for managing Arch Linux package state with `paru`.

```bash
arch-pkg required-by <package>
arch-pkg mark-as-explicit <package>
arch-pkg list-explicit
arch-pkg list-orphans
```

Can inspect package dependencies, mark packages as explicitly installed, and list explicit or orphaned packages.

## Requirements

* `python3`
* `paru`
