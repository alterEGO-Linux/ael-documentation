<!--
=============================================================================== 
INFO
===============================================================================
[/ael-documentation/components/ael-bin/commands/virtual-boxes.md]

Author      : Pascal Malouin (https://github.com/alterEGO-Linux)
Created     : 2026-09-28 19:42:34 UTC
Updated     : 2026-09-28 19:42:34 UTC
Description : virtual-boxes README.
-------------------------------------------------------------------------------
-->

# virtual-boxes

`virtual-boxes` is a simple VirtualBox virtual machine launcher for AlterEGO Linux.

It retrieves the virtual machines registered with VirtualBox, converts the VM information to structured JSON, and uses [AEL//Fuzz](https://github.com/alterEGO-Linux/ael-fuzz) with its QuickShell frontend to select a machine.

The selected VM is identified by its VirtualBox UUID and started using `VBoxManage`.

## Installation

From AEL//Bin, run the installer.

```bash
./install.sh --virtual-boxes
```

The application will be installed in the `AEL_BIN` or in `~/.local/bin`.

### Manual installation

Copy the script to `$AEL_BIN`:

```bash
cp virtual-boxes "$AEL_BIN/virtual-boxes"
chmod +x "$AEL_BIN/virtual-boxes"
```

The default value of `$AEL_BIN` is:

```text
~/.local/bin
```

`$AEL_BIN` must be included in `$PATH`.

For an AEL installation, the required path variables are normally provided by `.aelcore`.

The script also requires AEL BashLib. Its location is provided through:

```bash
$AEL_BASHLIB
```

The default AEL location is:

```text
~/.local/share/ael/ael-bashlib
```

For a non-AEL installation, these variables can be defined manually in the appropriate shell configuration file.

For example:

```bash
export AEL_BIN="$HOME/.local/bin"
export AEL_BASHLIB="$HOME/ael/ael-bashlib"
```

The required applications must also be installed and available in `$PATH`. See [Requirements](#requirements).

## Uninstallation

Run the following from AEL//bin.

```bash
./uninstall --virtual-boxes
```

Dependencies are not removed automatically because they may be used by other AEL components.

## Options and Usage

Run:

```bash
virtual-boxes
```

The available VirtualBox virtual machines are displayed through the AEL//Fuzz QuickShell frontend.

Select a virtual machine and press `Enter`.

`virtual-boxes` currently has no command-line options.

## Requirements

- AEL BashLib — see documentation <https://github.com/alterEGO-Linux/ael-documentation/components/ael-bashlib/INDEX.md>
- AEL//Fuzz — see documentation <https://github.com/alterEGO-Linux/ael-documentation/components/ael-fuzz/INDEX.md>
- `bash`
- VirtualBox — provides `VBoxManage` and manages the virtual machines.
- `awk` — extracts VM names and UUIDs from `VBoxManage list vms`.
- `jq` — converts the extracted VM information to JSON.

The script `virtual-boxes` verifies the command dependencies.

## Future Development

Possible future improvements include:

- Display additional VirtualBox information as AEL//Fuzz metadata.
- Indicate whether a VM is currently running.
- Add actions for starting, stopping, pausing, or resuming virtual machines.
- Add an optional AEL//Fuzz preview showing VM details.

## Resources

- AEL//Documentation - <https://github.com/alterEGO-Linux/ael-documentation>
- [AEL//Fuzz](https://github.com/alterEGO-Linux/ael-fuzz)
- [VirtualBox](https://www.virtualbox.org/)
