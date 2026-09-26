<!--
===============================================================================
INFO
===============================================================================
[/ael-documentation/components/ael-bin/commands/network-switch.md]

Author      : Pascal Malouin (https://github.com/alterEGO-Linux)
Created     : 2026-09-26 15:18:12 UTC
Updated     : 2026-09-26 15:18:16 UTC
Description : network-switch README.
-------------------------------------------------------------------------------
-->

# network-switch

Quickly enable or disable network connectivity by controlling the `NetworkManager` service.

```bash
network-switch --off
network-switch --on
```

When networking is enabled, NetworkManager handles reconnection using its configured connections and autoconnect settings.

Successful operations generate a desktop notification using `ael-notify`, with `notify-send` as a fallback.

```bash
network-switch --help
```

## Requirements

* AEL//Bash library (`$AEL_BASHLIB`).
* `NetworkManager`
* `systemctl`
* `sudo`
* `ael-notify` or `notify-send` for desktop notifications.

## Resources

* [NetworkManager](https://networkmanager.dev/)
* [AEL//Documentation](https://github.com/alterEGO-Linux/ael-documentation)
