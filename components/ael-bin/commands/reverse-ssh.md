<!--
=============================================================================== 
INFO
===============================================================================
[/ael-documentation/components/ael-bin/commands/reverse-ssh.md]

Author      : Pascal Malouin (https://github.com/alterEGO-Linux)
Assisted by : ChatGPT (OpenAI)
Created     : 2026-10-05 19:16:54 UTC
Updated     : 2026-10-05 19:16:54 UTC
Description : reverse-ssh README.
-------------------------------------------------------------------------------
-->

`reverse-ssh` is a small Bash wrapper for establishing a persistent SSH reverse tunnel from a remote machine to another SSH server.

It is intended for situations where the remote machine cannot accept a direct incoming SSH connection, but can establish an outgoing SSH connection to a reachable machine.

## Installation

Copy `reverse-ssh` to a directory in your `PATH` and make it executable:

```bash
chmod +x reverse-ssh
```

## Uninstallation

Remove the `reverse-ssh` script from the location where it was installed.

## Options and Usage

Run `reverse-ssh` on the remote machine:

```bash
reverse-ssh user@home_address:port
```

Where:

- `user` is the SSH user on the reachable home/server machine.
- `home_address` is the hostname or IP address of that machine.
- `port` is the TCP port that will be opened on that machine for the reverse tunnel.

For example:

```bash
reverse-ssh neot@example.com:6666
```

Then, on the home/server machine, connect to the remote machine through the tunnel:

```bash
ssh -p 6666 localhost
```

Add the username used on the remote device if different from the home username.

```bash
ssh -p 6666 morpheus@localhost
```

Show the reverse SSH tunnels owned by the current user:

```bash
reverse-ssh status
```

Stop a tunnel by its remote listening port:

```bash
reverse-ssh kill 6666
```

The kill option will prevent the connection to immediately reconnect.

Show the built-in help:

```bash
reverse-ssh --help
```

## How Reverse SSH Works

A normal SSH connection is initiated by the client toward an SSH server:

```text
remote machine  ───── SSH connection ─────>  home/server:22
```

A reverse SSH tunnel uses that existing outbound SSH connection to create a listening port on the SSH server side. Connections made to that port are forwarded back through the encrypted SSH connection to a host and port reachable from the remote machine.

`reverse-ssh` uses OpenSSH remote port forwarding with `-R`:

```bash
ssh user@home_address -R port:localhost:22
```

Conceptually:

```text
REMOTE MACHINE                              HOME / SERVER
──────────────                              ─────────────

SSH server :22                              SSH server :22
      ▲                                           ▲
      │                                           │
      │        outbound SSH connection            │
      └──────────────────────────────────────────>│
                                                  │
                                           localhost:port
                                                  │
                         reverse SSH tunnel       │
      ┌───────────────────────────────────────────┘
      │
      ▼
SSH server :22
```

The `-R` option tells the home/server SSH daemon to listen on the requested port and forward connections through the SSH tunnel to `localhost:22` as seen from the remote machine.

For example:

```bash
reverse-ssh neo@example.com:6666
```

establishes an SSH connection to `example.com` and requests this remote forwarding:

```text
example.com:6666 -> SSH tunnel -> remote machine localhost:22
```

From `example.com`, running:

```bash
ssh -p 6666 localhost
```

connects to port `6666` on the server. SSH forwards that connection through the existing tunnel to port `22` on the remote machine.

By default, OpenSSH normally binds a remote forward to the server's loopback interface. This is useful for this design because the reverse SSH port is intended to be reached locally from the home/server machine rather than exposed directly to other hosts.

### Keeping the SSH connection alive

The script uses:

```text
ServerAliveInterval=60
```

When no data has been received from the SSH server, the SSH client periodically sends a message through the encrypted connection. This helps detect broken connections and can prevent an otherwise idle connection from being dropped by some network devices.

The SSH process remains in the foreground under the `reverse-ssh` wrapper. If the SSH connection ends, the wrapper waits 10 seconds and attempts to reconnect. Reconnection attempts are reported, and OpenSSH's `LocalCommand` reports when the connection has been successfully established or re-established.

Before starting a tunnel, `reverse-ssh` also checks the current user's SSH processes for an existing reverse tunnel using the requested port. This prevents the wrapper from repeatedly attempting to claim a port already used by one of the user's existing reverse SSH connections.

## SSH Keys

Password authentication can be used, but it limits unattended reconnection because SSH may request the password again whenever a new connection is established.

For automatic reconnection, SSH public-key authentication is recommended.

On the remote machine, create an SSH key if required:

```bash
ssh-keygen -t ed25519
```

Copy the public key to the home/server machine:

```bash
ssh-copy-id user@home_address
```

Verify that the remote machine can connect without requiring an interactive password before relying on `reverse-ssh` for unattended operation:

```bash
ssh user@home_address
```

## Requirements

The script intentionally has very few requirements:

- Bash
- OpenSSH client (`ssh`)
- `ps`
- An SSH server reachable from the remote machine
- An SSH server running on port `22` of the remote machine for the default forwarding target

## Resources

- OpenSSH `ssh(1)` manual — <https://www.man7.org/linux/man-pages/man1/ssh.1.html>
- Server Fault — *SSH remote port forwarding failed* - <https://serverfault.com/questions/595323/ssh-remote-port-forwarding-failed>
- SSH Academy — *SSH Port Forwarding* - <https://www.ssh.com/academy/ssh/tunneling-example>
- How-To Geek — *What Is Reverse SSH Tunneling?* - <https://www.howtogeek.com/428413/what-is-reverse-ssh-tunneling-and-how-to-use-it/>
