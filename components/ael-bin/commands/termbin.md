<!--
# termbin - README
# author  : Pascal Malouin (https://github.com/EGOUID0)
# project : https://github.com/alterEGO-Linux/ael-bin
# created : 2026-11-13
-->

# termbin

A simple AEL//Bin command-line utility for sending text to [termbin.com](https://termbin.com), with optional persistent URL history.

`termbin` can create a paste, remember the returned URL, and display previously logged URLs.

## Features

- Send text directly from the command line.
- Accept input through `stdin`.
- Log generated URLs for later retrieval.
- Store URL history using the XDG state convention.
- Suppress URL output when logging with `--log-only`.
- Uses AEL//BashLib for dependency checking and messages.
- Can be executed directly or sourced as a Bash function.

## Usage

```text
termbin <action> [message...] [options]
```

### Actions

| Action | Description |
|---|---|
| `create` | Create a termbin and output the returned URL. |
| `log` | Create a termbin, output the URL, and save the URL to history. |
| `history` | Display previously logged termbin URLs. |

### Options

| Option | Description |
|---|---|
| `--log-only` | With `log`, save the returned URL without displaying it. |
| `-h`, `--help` | Display help. |

## Examples

Create a termbin:

```bash
termbin create "Hello, world!"
```

The returned URL is written to stdout:

```text
https://termbin.com/jukkt
```

Input does not need to be quoted:

```bash
termbin create Hello, world!
```

Input can also be piped through `stdin`:

```bash
echo "Hello, world!" | termbin create
```

or:

```bash
cat error.log | termbin create
```

This makes it useful for sharing command output:

```bash
pacman -Q | termbin create
```

or both stdout and stderr:

```bash
some-command 2>&1 | termbin create
```

## Logging URLs

Termbin URLs can be difficult to recover after they have been created. The `log` action provides persistent local URL history.

```bash
termbin log "Hello, world!"
```

This:

1. sends the content to termbin.com;
2. outputs the returned URL;
3. records the URL with a timestamp in the history file.

Example:

```text
[+] URL logged to: /home/user/.local/state/termbin/history
https://termbin.com/jukkt
```

The informational message is written to `stderr`, while the URL remains on `stdout`.

This means command substitution remains useful:

```bash
url="$(termbin log "Hello, world!")"
```

`$url` contains only the returned URL.

## Log Only

Use `--log-only` when the URL should be saved without being written to stdout:

```bash
termbin log "Hello, world!" --log-only
```

It also works with piped input:

```bash
some-command 2>&1 | termbin log --log-only
```

`--log-only` is an option of the `log` action and cannot be used with `create`.

## History

Display all previously logged URLs with:

```bash
termbin history
```

Example:

```text
2026-10-06 09:22:52 https://termbin.com/jukkt
2026-10-06 10:14:07 https://termbin.com/abcd1
2026-10-06 11:32:41 https://termbin.com/xyz12
```

The history file is stored at:

```text
${XDG_STATE_HOME:-$HOME/.local/state}/termbin/history
```

With the default XDG configuration, this resolves to:

```text
~/.local/state/termbin/history
```

The history file contains only the timestamp and returned URL. The content sent to termbin is **not** stored locally by `termbin`.

## Dependencies

|||
|---|---|
|AEL//bashlib|`termbin` uses AEL//bashlib for common functionalities. See [AEL//bashlib documentation](https://github.com/alterEGO-Linux/ael-documentation/blob/main/components/ael-bashlib/INDEX.md) for setup.|
|`nc`||

## Sourcing

The script can also be sourced into the current Bash environment for convenience:

```bash
source ~/.local/bin/termbin
```

## License

Part of the **alterEGO Linux (AEL)** project.

Copyright © Pascal Malouin / alterEGO Linux.
