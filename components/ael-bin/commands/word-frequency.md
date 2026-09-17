<!--
=============================================================================== 
INFO
===============================================================================
[/ael-documentation/components/ael-bin/commands/word-frequency.md]

Author      : Pascal Malouin (https://github.com/alterEGO-Linux)
Created     : 2026-09-17 11:24:37 UTC
Updated     : 2026-09-17 11:24:37 UTC
Description : word-frequency.
-------------------------------------------------------------------------------
-->

# word-frequency

Counts word occurrences from a file or standard input and displays them by frequency or alphabetically.

Supports case-sensitive counting, common stopword filtering, custom stopword files, alphabetical sorting, and output without occurrence counts.

Use `--significant` to remove common English words and highlight the most meaningful vocabulary in a text.

## Installation

Requires Python 3.

Make the script executable:

```bash
chmod +x word-frequency
```

Then place it somewhere in your `PATH`, for example:

```bash
sudo install -m 755 word-frequency /usr/local/bin/word-frequency
```

## Usage

Read text from a file:

```bash
word-frequency -i document.txt
```

Read text from standard input:

```bash
cat document.txt | word-frequency
curl https://www.gutenberg.org/cache/epub/1342/pg1342.txt | word-frequency --significant | head -n 50
```

Show only significant words by filtering common English stopwords:

```bash
word-frequency -i document.txt --significant
```

For all available options:

```bash
word-frequency --help
```

## Requirements

* `python3`
