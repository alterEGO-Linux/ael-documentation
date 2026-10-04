<!--
=============================================================================== 
INFO
===============================================================================
[/ael-documentation/components/ael-bin/commands/py-server.md]

Author      : Pascal Malouin (https://github.com/alterEGO-Linux)
Assisted by : ChatGPT (OpenAI)
Created     : 2026-10-04 16:11:41 UTC
Updated     : 2026-10-04 16:11:41 UTC
Description : py-server README.md
-------------------------------------------------------------------------------
-->

# py-server

`py-server` is a small AEL utility that starts a Python HTTP server in the current directory.

The command automatically searches for an available TCP port between `8000` and `8010`, then starts Python's built-in `http.server` module using the first available port.

This is useful for quickly serving files from a directory without manually selecting a port or configuring a web server.

## Installation

`py-server` is part of [AEL//bin](https://github.com/alterEGO-Linux/ael-bin) and is normally installed using the AEL//bin installation script.

```bash
git clone https://github.com/alterEGO-Linux/ael-bin.git
cd ael-bin
./install.sh
```

`py-server` requires [AEL//bashlib](https://github.com/alterEGO-Linux/ael-bashlib).

The recommended location for AEL//bashlib is:

```text
~/.local/share/ael/ael-bashlib
```

If AEL//bashlib is installed somewhere else, set `$AEL_BASHLIB` to its location:

```bash
export AEL_BASHLIB="/path/to/ael-bashlib"
```

To make the setting persistent, add the export to the appropriate shell configuration file.

If `$AEL_BASHLIB` is not set, `py-server` attempts to use:

```text
~/.local/share/ael/ael-bashlib
```

If AEL//bashlib cannot be found, `py-server` exits with an error.

## Uninstallation

When installed as part of AEL//bin, use the provided uninstallation script:

```bash
./uninstall.sh
```

Refer to the AEL//bin documentation for options that control which components are removed.

## Port Selection

`py-server` searches the following ports in order:

```text
8000
8001
8002
8003
8004
8005
8006
8007
8008
8009
8010
```

The first available port is selected automatically.

No port needs to be specified by the user.

## Options and Usage

Run `py-server` from the directory that should be served:

```bash
cd ~/some/directory
py-server
```

For example:

```bash
cd ~/Downloads
py-server
```

If port `8000` is available, the command reports:

```text
py-server: Starting HTTP server on port 8000
```

Python's built-in HTTP server is then started:

```bash
python -m http.server 8000
```

The contents of the current directory can be accessed from the local machine at:

```text
http://localhost:8000/
```

Other devices may also be able to access the server using the host's IP address, provided that the network and firewall configuration permit incoming connections:

```text
http://<host-ip>:8000/
```

Stop the server with:

```text
Ctrl+C
```

### Automatic Port Selection

If port `8000` is already in use, `py-server` tries `8001`, followed by `8002`, and continues through the configured port range until an available port is found.

For example:

```text
8000 → in use
8001 → in use
8002 → available
```

The server will start on port `8002`.

## Requirements

* Bash
* Python
* `netstat`
* `grep`
* AEL//bashlib
* A working network stack
* `sudo` access for the current port-detection implementation

AEL//bashlib is used to provide application dependency checking and standardized AEL messages.

## Future Development

This section is not intended to be a development roadmap, but rather a list of ideas and possible improvements for the application.

* Allow a preferred port to be supplied from the command line.
* Allow the port range to be configured.

## Resources

* [AEL//Documentation](https://github.com/alterEGO-Linux/ael-documentation)
* [AEL//Bin](https://github.com/alterEGO-Linux/ael-bin)
* [AEL//BashLib](https://github.com/alterEGO-Linux/ael-bashlib)
* [Python `http.server` documentation](https://docs.python.org/3/library/http.server.html)
