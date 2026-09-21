<!--
=============================================================================== 
INFO
===============================================================================
[/ael-documentation/components/ael-bin/commands/whoisweb.md]

Author      : Pascal Malouin (https://github.com/alterEGO-Linux)
Created     : 2026-09-18 11:25:12 UTC
Updated     : 2026-09-18 11:25:12 UTC
Description : whoisweb
-------------------------------------------------------------------------------
-->

# whoisweb

Queries WHOIS information over the web when the traditional WHOIS service on TCP port 43 is blocked or unavailable.

The command uses the whoisjs.com API to retrieve WHOIS data and formats the raw response for terminal output.

```bash
whoisweb example.com
```

Useful on restricted corporate, VPN, or public networks where direct WHOIS queries are not permitted.

## Requirements

* AEL//Bash library (`~/.ael/lib/bash/`).
* `curl`
* `jq`
* `sed`

## To Do List

* Make AEL//Bash library path flexible and configurable.
