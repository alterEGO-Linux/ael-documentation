<!--
===============================================================================
INFO
===============================================================================
[/ael-documentation/components/ael-bin/commands/ps-grep.md]

Author      : Pascal Malouin (https://github.com/alterEGO-Linux)
Created     : 2026-09-26 13:58:04 UTC
Updated     : 2026-09-26 13:58:08 UTC
Description : Search and inspect running processes.
-------------------------------------------------------------------------------
-->

# ps-grep

Search and inspect running processes using a compact and readable interface around `ps`.

```bash
ps-grep <pattern>
```

By default, `ps-grep` displays a summary containing the user, PID, CPU usage, memory usage, resident memory (RSS), and process command.

```text
USER              PID   %CPU   %MEM        RSS  COMMAND
------------  -------- ------ ------ ----------  -------
neo             15464    1.3   11.3  894.6 MiB  Isolated
neo              4523   34.0    9.1  714.6 MiB  zen-bin
neo              5070    1.7    7.9  623.4 MiB  Isolated
```

RSS values are automatically converted from KiB to a human-readable format.

## Usage

```bash
ps-grep [options] <pattern>
```

For example:

```bash
ps-grep zen
```

The search is case-insensitive and matches against the complete process information, including the command line.

## Display Modes

### Summary

```bash
ps-grep zen
ps-grep zen --summary
```

`--summary` is the default display mode and provides a compact overview of matching processes.

The following fields are displayed:

* `USER` — Process owner.
* `PID` — Process ID.
* `%CPU` — CPU utilization.
* `%MEM` — Percentage of physical memory.
* `RSS` — Resident Set Size in human-readable units.
* `COMMAND` — Process command or process role.

### Stack

```bash
ps-grep zen --stack
```

Displays each process as a vertical record.

```text
USER      neo  
PID       4523
PPID      1
CPU       34.0%
MEM       9.1%
RSS       714.6 MiB
START     Sep25
TIME      273:05
COMMAND   zen-bin
```

This mode includes additional information such as the parent PID, start time, and accumulated CPU time.

### Full

```bash
ps-grep zen --full
```

Displays the traditional full `ps aux` output for matching processes.

This mode retains the complete command line and highlights the matching search pattern.

## Sorting

Results can be sorted using `--sort`.

### Resident memory

```bash
ps-grep zen --sort=RSS
```

Sorts processes by RSS from highest to lowest.

### CPU usage

```bash
ps-grep zen --sort=CPU
```

Sorts processes by CPU utilization from highest to lowest.

### Memory percentage

```bash
ps-grep zen --sort=MEM
```

Sorts processes by memory percentage from highest to lowest.

### Process ID

```bash
ps-grep zen --sort=PID
```

Sorts processes by PID from lowest to highest.

Sorting can be combined with the different display modes:

```bash
ps-grep zen --stack --sort=RSS
ps-grep zen --full --sort=CPU
```

## Verbose

```bash
ps-grep zen --verbose
```

Adds additional process information without expanding the main summary table.

For each process, the following fields are added:

* `PPID` — Parent process ID.
* `START` — Process start time or date.
* `TIME` — Accumulated CPU time.
* `ARGS` — Complete process command line.

For example:

```text
neo             15464    1.3   11.3  894.6 MiB  Isolated
  PPID     4523
  START    Sep25
  TIME     10:12
  ARGS     /opt/zen-browser-bin/zen-bin -contentproc ...
```

`--verbose` can also be used with `--stack` to include the complete command line.

## Total

```bash
ps-grep zen --total
```

Displays the number of matching processes and their combined RSS.

```text
------------------------------------------------------------
16 processes · 4.4 GiB RSS
```

This is particularly useful for applications that use multiple processes, such as web browsers.

RSS represents resident memory and may include shared memory pages, so the total should be treated as a process-group memory indicator rather than the application's exact unique physical memory consumption.

Options can be combined:

```bash
ps-grep zen --sort=RSS --total
```

Or:

```bash
ps-grep zen --sort=RSS --verbose --total
```

## Options

```text
--summary          Compact process table (default).
--stack            Show each process as a vertical record.
--full             Show full ps output.

--sort=RSS         Sort by resident memory, highest first.
--sort=CPU         Sort by CPU usage, highest first.
--sort=MEM         Sort by memory usage, highest first.
--sort=PID         Sort by PID, lowest first.

--verbose, -v      Show additional process information.
--total            Show process count and total RSS.
--help, -h         Show help.
```

## Requirements

* AEL//Bash library (`${AEL_BASHLIB}`).
* `ps`
* `grep`
* `awk`
* `sort`

## Examples

Find processes associated with Zen Browser:

```bash
ps-grep zen
```

Find the largest Zen processes by resident memory:

```bash
ps-grep zen --sort=RSS
```

Display the total resident memory used by matching processes:

```bash
ps-grep zen --sort=RSS --total
```

Investigate the command lines of memory-heavy processes:

```bash
ps-grep zen --sort=RSS --verbose
```

Display detailed process records:

```bash
ps-grep zen --stack --sort=RSS --total
```

Fall back to the complete `ps aux` representation:

```bash
ps-grep zen --full
```

## To Do List

* Consider additional sort fields where useful.
* Consider filtering by PID, user, CPU, or memory thresholds.
* Consider optional color highlighting for high CPU or memory usage.

## Resources

* [procps-ng](https://gitlab.com/procps-ng/procps)
* [ps(1) manual page](https://man.archlinux.org/man/ps.1)
* [Full AEL//Documentation](https://github.com/alterEGO-Linux/ael-documentation)
