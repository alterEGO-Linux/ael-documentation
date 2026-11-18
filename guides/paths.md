<!--
# AEL//documentation / Guides / Path 
# author  : Pascal Malouin (https://github.com/EGOUID0)
# project : https://github.com/alterEGO-Linux/ael-documentation
# created : 2026-09-15
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

## Application Configuration: `AEL_CONFIG`

Configuration files for applications developed within the **AEL ecosystem** are stored under `~/.config/ael/` by default.

Each application maintains its own subdirectory to ensure configuration isolation and consistency.

```text
~/.config/ael/
├── ael-colors/
│   └── config.toml
├── ael-fuzz/
│   └── config.toml
└── ael-containers/
    ├── config.toml
    └── private/
```

### Private Configuration

Applications that support user customization may provide a `private/` directory within their configuration directory.

This directory is intended for user-specific settings and customizations that should be preserved independently of the application's lifecycle.

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
