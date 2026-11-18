<!--
# easyrdp - README
# author      : Pascal Malouin (https://github.com/EGOUID0)
# assisted by : ChatGPT (OpenAI)
# project     : https://github.com/alterEGO-Linux/ael-documentation)
# created     : 2026-11-15
-->

# easyrdp

`easyrdp` is a simple AEL wrapper around FreeRDP (`xfreerdp3`) for connecting to remote Windows desktops using reusable configuration files.

It supports direct connections, optional RDP gateways, clipboard and sound redirection, USB redirection, fullscreen mode, and automatic reconnection. When no configuration file is specified, it uses AEL//fuzz with its Quickshell frontend to select one.

## Installation

`easyrdp` is part of [AEL//bin](https://github.com/alterEGO-Linux/ael-bin) and is normally installed on AEL ecosystem through its installation script:

```bash
git clone https://github.com/alterEGO-Linux/ael-bin.git
cd ael-bin
./install.sh
```

It can also be installed individually:

```bash
./install.sh --easyrdp
```

The command requires [AEL//bashlib](https://github.com/alterEGO-Linux/ael-documentation/blob/main/components/ael-bashlib/INDEX.md).

## Uninstallation

When installed as part of AEL//bin, use:

```bash
./uninstall.sh --easyrdp
```

Refer to AEL//bin's uninstallation options for removal behavior. Connection profiles are stored under the user-managed `private/` directory and should be preserved unless explicitly removed. Check the installed uninstaller's behavior before relying on this preservation policy.

## Configuration

Connection profiles are stored by convention in:

```text
~/.config/ael/easyrdp/private/
```

The directory is created automatically when `easyrdp` starts. Each regular file directly inside it is eligible for selection by AEL//fuzz; the script does not filter by filename extension or search subdirectories.

Example layout:

```text
~/.config/ael/easyrdp/
└── private/
    ├── office.conf
    └── workstation.conf
```

Create a profile such as `~/.config/ael/easyrdp/private/office.conf`:

```bash
user="a_regular_user"
domain="MyDomain"
server="my_domain.com"
# password="optional_password"

# Optional RDP gateway
gateway_server="remote.gateway.ca"
gateway_user="gateway_user"
# gateway_password="optional_gateway_password"

clipboard="yes"
sound="yes"
usb="no"
fullscreen="no"
reconnect=20
```

Remove or comment out the gateway settings when no gateway is needed.

**Important:** Profiles are sourced as Bash code, not parsed as TOML or inert key-value data. Only use trusted configuration files; arbitrary shell commands in a profile would execute with your user privileges.

### Configuration options

| Option | Default | Description |
| --- | --- | --- |
| `user` | Required | Remote account username. |
| `domain` | Required | Remote authentication domain. |
| `server` | Required | Remote RDP server address or hostname. |
| `password` | Unset | Optional RDP password. |
| `gateway_server` | Unset | Optional RDP gateway hostname. |
| `gateway_user` | Required if gateway is set | Gateway account username. |
| `gateway_password` | Unset | Optional gateway password. |
| `clipboard` | `yes` | Enable clipboard redirection when set to `yes`. |
| `sound` | `yes` | Enable sound redirection when set to `yes`. |
| `usb` | `no` | Enable automatic USB redirection when set to `yes`. |
| `fullscreen` | `no` | Start in fullscreen mode when set to `yes`. |
| `reconnect` | `20` | Enable automatic reconnection and set the maximum retry count. An empty value disables the reconnection arguments. |

Boolean-style options are case-sensitive: only the literal value `yes` enables them.

## Options and Usage

```text
easyrdp
easyrdp -c CONFIG_FILE
easyrdp --config CONFIG_FILE
easyrdp -h
easyrdp --help
```

Start the interactive profile selector:

```bash
easyrdp
```

This uses `ael-fuzz --frontend quickshell` to choose a profile from `~/.config/ael/easyrdp/private/`. Cancelling the selector exits without starting FreeRDP.

Connect with an explicit profile:

```bash
easyrdp --config ~/.config/ael/easyrdp/private/office.conf
```

The short form is equivalent:

```bash
easyrdp -c ~/.config/ael/easyrdp/private/office.conf
```

An explicit profile path can point outside the default `private/` directory.

Display help with `easyrdp --help`.

## Password Handling and Security

Both `password` and `gateway_password` are optional. If either is unset or empty, EasyRDP omits that password from the corresponding FreeRDP arguments. FreeRDP then determines whether and how to request credentials or use an available authentication mechanism.

- **Terminal launch:** FreeRDP may request a missing password interactively, depending on its authentication path and environment.
- **Desktop launcher (`.desktop`):** No terminal is normally available. If authentication requires a terminal prompt, the connection may fail. EasyRDP does not currently implement its own graphical password dialog.
- **Configured password:** EasyRDP supplies it to FreeRDP, avoiding a missing-password prompt for that credential.

**Security implications:** Passwords in profiles are stored as plaintext. The current implementation passes configured passwords using FreeRDP command-line arguments (`/p:` for the remote password and `p:` within `/gateway:` for the gateway password). Such arguments may be exposed through process inspection and diagnostic tools, even when the profile file has restrictive permissions.

If you store credentials in a profile, restrict access to it:

```bash
chmod 600 ~/.config/ael/easyrdp/private/office.conf
```

Do not commit credential-bearing profiles to version control. File permissions reduce file exposure but **do not** eliminate command-line argument exposure. Prefer omitting stored passwords when an interactive or other secure authentication mechanism is available.

## Requirements

- Bash
- FreeRDP 3 (`xfreerdp3`)
- AEL//bashlib
- AEL//fuzz (`ael-fuzz`) with its Quickshell frontend, **only when selecting a profile interactively**
- `find` for interactive profile discovery
- Network access to the RDP server and, if configured, the gateway

## Future Development

Possible improvements include:

- Graphical password prompting for desktop launches.
- Safer password transfer to FreeRDP, avoiding credentials in command-line arguments.
- Additional configuration-selection frontends beyond AEL//fuzz.

### Alternative: Remmina

EasyRDP is a lightweight wrapper for FreeRDP, designed for users who prefer simple configuration files and command-line integration.

For a more complete graphical RDP experience, **[Remmina](https://remmina.org/)** is generally the better choice. It provides connection profiles, graphical configuration, credential management, and support for multiple remote desktop protocols.

**In short:** EasyRDP is for those who enjoy scripting their connections. Remmina is for those who just want them to work. ;-)

## Resources

- [AEL//documentation](https://github.com/alterEGO-Linux/ael-documentation)
- [AEL//bin](https://github.com/alterEGO-Linux/ael-bin)
- [AEL//bashlib](https://github.com/alterEGO-Linux/ael-documentation/blob/main/components/ael-bashlib/INDEX.md)
- [FreeRDP](https://www.freerdp.com/)
