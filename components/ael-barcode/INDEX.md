<!--
=============================================================================== 
INFO
===============================================================================
[/ael-documentation/components/ael-barcode/INDEX.md]

Author      : Pascal Malouin (https://github.com/alterEGO-Linux)
Created     : 2026-09-25 13:46:24 UTC
Updated     : 2026-09-25 13:46:24 UTC
Description : AEL//Barcode README.
-------------------------------------------------------------------------------
-->

# AEL//Barcode

AEL//Barcode is a universal streaming barcode decoder from AlterEGO Linux (AEL).
It scans image files and PDF documents, detects one or more barcodes per image or
PDF page, and supports both human-friendly and machine-readable output.

## Features

- Decode barcodes from PDF and image files.
- Recursive directory scanning.
- PDF processing one page at a time to keep memory use bounded.
- Detect zero, one, or multiple barcodes per image/page.
- Status values: `OK`, `No barcode found`, and `Multiple barcodes detected`.
- Barcode metadata: data, symbology, decoder quality, orientation, and rectangle.
- Plain human and Rich terminal output.
- `value`, JSON, and streaming JSONL output for scripts and pipelines.
- Filter by barcode type or regular expression.
- Optional decoder-quality filtering.
- Optional scanning-session summary with counts, symbologies, and elapsed time.

AEL//Barcode currently uses ZBar through `pyzbar`. Supported symbologies therefore
depend on the installed ZBar version.

## Installation

AEL//Barcode targets AEL ecosystem, but can, in theory, run on any Arch Linux environment.

For other Linux flavor, you will have to tweak the install/uninstall script to adjust to your distro.

Clone or extract the repository, then run:

```bash
./install.sh
```

The installer checks the required Arch packages and installs missing ones with
`pacman`:

- `python`
- `zbar`
- `poppler`

It then creates an isolated Python virtual environment under:

```text
${XDG_DATA_HOME:-$HOME/.local/share}/ael-barcode/venv
```

and creates the launcher:

```text
~/.local/bin/ael-barcode
```

Make sure `~/.local/bin` is in `PATH`.

## Usage

Scan one file:

```bash
ael-barcode document.pdf
```

Scan a directory recursively:

```bash
ael-barcode ~/tmp/barcode_test/
```

Use Rich output:

```bash
ael-barcode ~/tmp/barcode_test/ --output rich
```

Show a session summary:

```bash
ael-barcode ~/tmp/barcode_test/ --output rich --summary
```

Filter by barcode type:

```bash
ael-barcode scans/ --type QRCODE
```

Multiple types may be requested:

```bash
ael-barcode scans/ --type QRCODE --type CODE39
```

Filter decoded values with a regular expression:

```bash
ael-barcode scans/ --match '^WS[0-9]{8}-[0-9]+$'
```

Change PDF rendering resolution:

```bash
ael-barcode document.pdf --dpi 300
```

## Output formats

### human

Default portable terminal output:

```bash
ael-barcode document.pdf --output human
```

### rich

Rich interactive terminal presentation:

```bash
ael-barcode document.pdf --output rich
```

### value

Print only decoded values:

```bash
ael-barcode document.pdf --output value
```

### json

Emit one JSON array containing scan results:

```bash
ael-barcode document.pdf --output json
```

### jsonl

Emit one JSON object per scanned image/page as soon as it is available:

```bash
ael-barcode scans/ --output jsonl
```

This is useful in pipelines:

```bash
ael-barcode scans/ --output jsonl | jq .
```

When `--summary` is combined with `value`, `json`, or `jsonl`, the summary is
written to stderr so stdout remains safe for pipelines.

## Result model

One result represents one image or one PDF page.

Machine-readable statuses are:

- `ok` — exactly one matching barcode was detected.
- `not_found` — no matching barcode was detected.
- `multiple` — more than one matching barcode was detected.

Example JSONL result:

```json
{"file":"/tmp/test.png","page":null,"status":"ok","barcodes":[{"data":"AEL-CODE39-TEST","type":"CODE39","quality":100,"orientation":"UP","rect":{"left":60,"top":60,"width":440,"height":99}}]}
```

Status is calculated after filters are applied. For example, an image containing
a QR code and CODE39 barcode reports `multiple` normally, but may report `ok`
when scanned with `--type QRCODE`.

## Decoder quality

`quality` comes from the underlying ZBar decoder. It is **not a percentage and
not a universal confidence score**. Values should not be compared across
symbologies. During development, a clean generated QR code returned quality `1`
while a clean generated CODE39 returned quality `100`.

For that reason, `--min-quality` is an advanced diagnostic filter and should be
used only when its behavior is understood for the target symbology and input.

## Tested

Version 0.2.0 has been tested with:

- CODE39
- Rotated CODE39
- CODE128
- QR Code
- Mixed QR Code + CODE39 in one image
- PDF input
- PNG input
- Multiple detections
- No-barcode input

## Uninstallation

From the repository:

```bash
./uninstall.sh
```

This removes the AEL//Barcode virtual environment and the `~/.local/bin/ael-barcode`
launcher. System packages installed through `pacman` are intentionally left in
place.

## Requirements

* `poppler`
* `python`
* `zbar`

## AEL//Documentation

The canonical AEL//Barcode documentation:

```text
AEL//Documentation: /components/ael-barcode/INDEX.md
```

Full AEL documentation can be found at <https://github.com/alterEGO-Linux/ael-documentation>
