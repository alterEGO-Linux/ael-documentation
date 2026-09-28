<!--
=============================================================================== 
INFO
===============================================================================
 [/ael-documentation/guides/paths.md]

 Author      : Pascal Malouin (https://github.com/alterEGO-Linux)
 Created     : 2026-09-15 14:28:09 UTC
 Updated     : 2026-09-28 12:20:10 UTC
 Description : Guide: Path
-------------------------------------------------------------------------------
-->

# Paths

The AEL ecosystem is currently built on top of Arch Linux and Hyprland.

Whenever possible, AEL uses standard user-level locations for executables, configuration files, and other application data.

AEL also aims to leave the existing system intact. When an AEL component is uninstalled, its files should be removed without affecting files or configurations that existed before its installation.

All default AEL paths are defined in `.aelcore`.

For non-AEL users, the required paths and environment variables should be defined in the appropriate shell configuration file (for example, `.bashrc`).

| Variable | Description | Default |
| :-- | :-- | :-- |
| `$AEL_HOME` | Main directory for the AlterEGO Linux ecosystem. | `~/.ael` |
| `$AEL_BIN` | Directory containing executable files. This directory should be included in `$PATH`. | `~/.local/bin` |
| `$AEL_CONFIG` | Directory containing application configuration files. Applications should use their own subdirectory, such as `$AEL_CONFIG/goodapp/goodapp.conf`. | `~/.config` |
| `$AEL_BUILD` | Directory used to build projects and applications, including cloned Git repositories. | `$AEL_HOME/.build` |
| `$AEL_DATA` | Directory containing data files used by AEL, such as lists, TOML files, and JSON files. | `$AEL_HOME/data` |
| `$AEL_BASHLIB` | Directory containing the Bash library used by AEL. | `$AEL_HOME/lib/ael-bashlib` |
| `$AEL_PRIVATE` | User-level customization directory. | `$AEL_HOME/private` |

## Path Customization

AEL users can override the default paths by defining custom values in:

```text
$AEL_HOME/private/path
```

This file is intended for user-specific path customization and should take precedence over the default values defined by `.aelcore`.

For example:

```bash
export AEL_BIN="$HOME/bin"
export AEL_BUILD="$HOME/build"
export AEL_DATA="$HOME/.local/share/ael"
```

Only paths that need to be customized have to be defined. All other paths continue to use their AEL defaults.

User-specific path customizations should not require modifications to `.aelcore`. This keeps the core AEL configuration separate from local preferences and prevents user customizations from being overwritten by AEL updates.
