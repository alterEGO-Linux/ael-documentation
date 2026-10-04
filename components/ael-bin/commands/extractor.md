<!--
=============================================================================== 
INFO
===============================================================================
[/ael-documentation/components/ael-bin/commands/extractor.md]

Author      : Pascal Malouin (https://github.com/alterEGO-Linux)
Created     : 2026-10-04 14:13:30 UTC
Updated     : 2026-10-04 14:13:30 UTC
Description : extractor README.
-------------------------------------------------------------------------------
-->

# extractor

`extractor` is a universal archive extraction command designed for the AEL ecosystem.

It provides a single command for extracting common archive and compression formats while preventing archives from unexpectedly dropping multiple files into the current directory.

The command automatically determines an appropriate extraction directory based on the archive filename and its internal structure.

When possible, `extractor` relies on the "natural" utility used to extract or decompress a particular file type. For exemple `*.zip` -> `unzip`.

---

## Installation

`extractor` is installed from the AEL//bin install script:

```bash
cd ael-bin
./install.sh --extractor
```

See <https://github.com/alterEGO-Linux/ael-documentation/components/ael-bin/INDEX.md> for more details.

`extractor` uses AEL//bashlib for presentation and application check.

See <https://github.com/alterEGO-Linux/ael-documentation/components/ael-bashlib/INDEX.md> for installation and configuration details.

The exact application required depends on the archive format.

| Application | Formats |
|---|---|
| `tar` | `.tar`, `.tar.gz`, `.tgz`, `.tar.bz2`, `.tbz2`, `.tar.xz`, `.txz`, `.tar.zst`, `.tzst` |
| `gunzip` | `.gz` |
| `bunzip2` | `.bz2` |
| `unxz` | `.xz` |
| `unlzma` | `.lzma` |
| `uncompress` | `.Z` |
| `unzip` | `.zip` |
| `unrar` | `.rar` |
| `7z` | `.7z`, `.iso` |
| `cpio` | `.cpio` |

Dependencies are checked when required rather than requiring every supported extraction utility to be installed.

The external utility can be installed independently as needed.

## Usage

```bash
extractor <file1> [file2 ... fileN]
```

Multiple archives can be passed in a single command:

```bash
extractor archive.zip package.tar.gz backup.7z
```

Display the built-in help:

```bash
extractor --help
```

or:

```bash
extractor -h
```

---

## Extraction Behavior

For multi-file archives, `extractor` attempts to ensure that the extracted files are contained within one sensible top-level directory.

The destination directory is normally derived from the archive filename with the archive extension removed.

For example:

```text
project.tar.gz
```

normally extracts to:

```text
project/
```

### Archive Without a Top-Level Directory

If `project.tar.gz` contains:

```text
README.md
LICENSE
src/
docs/
```

`extractor` creates `project/` and extracts the archive into it:

```text
project/
├── README.md
├── LICENSE
├── src/
└── docs/
```

This prevents the archive from dropping files directly into the current directory.

### Archive With a Matching Top-Level Directory

If `project.tar.gz` already contains:

```text
project/
project/README.md
project/src/
project/src/main.rs
```

`extractor` recognizes that the archive already provides the desired directory.

The archive is therefore extracted into its parent directory, resulting in:

```text
project/
├── README.md
└── src/
    └── main.rs
```

instead of:

```text
project/
└── project/
    ├── README.md
    └── src/
```

The matching directory must correspond to the archive filename after its archive extension is removed.

For example:

```text
ael-fuzz.tar.gz
```

matches:

```text
ael-fuzz/
```

---

## Supported Formats

### Tar Archives

| Format | Description |
|---|---|
| `.tar` | Uncompressed tar archive |
| `.tar.gz` | gzip-compressed tar archive |
| `.tgz` | Alias for `.tar.gz` |
| `.tar.bz2` | bzip2-compressed tar archive |
| `.tbz2` | Alias for `.tar.bz2` |
| `.tar.xz` | xz-compressed tar archive |
| `.txz` | Alias for `.tar.xz` |
| `.tar.zst` | Zstandard-compressed tar archive |
| `.tzst` | Alias for `.tar.zst` |

### Single-File Compression

| Format | Description |
|---|---|
| `.gz` | gzip-compressed file |
| `.bz2` | bzip2-compressed file |
| `.xz` | xz-compressed file |
| `.lzma` | LZMA-compressed file |
| `.Z` | Legacy UNIX compress format |

Single-file compression formats are decompressed directly rather than placed inside a new directory.

For example:

```text
document.txt.gz
```

becomes:

```text
document.txt
```

### Other Archives

| Format | Description |
|---|---|
| `.zip` | ZIP archive |
| `.rar` | RAR archive |
| `.7z` | 7-Zip archive |
| `.iso` | ISO image |
| `.cpio` | cpio archive |

ISO images are extracted using `7z`; they are not mounted.

`cpio` archives are always extracted into a directory derived from the archive filename.

---

## Requirements

* AEL//bashlib <https://github.com/alterEGO-Linux/ael-documentation/components/ael-bashlib/INDEX.md>
* `bash`
* `tar` (as needed)
* `gunzip` (as needed)
* `bunzip2` (as needed)
* `unxz` (as needed)
* `unlzma` (as needed)
* `uncompress` (as needed)
* `unzip` (as needed)
* `unrar` (as needed)
* `7z` (as needed)
* `cpio` (as needed)

---

## Future Development

* Add an option to specify where to extract the archives. Right now, `extractor` will just extract in the current working directory.

---

## Resources

* AEL//documentation - <https://github.com/alterEGO-Linux/ael-documentation>
* AEL//bin - <https://github.com/alterEGO-Linux/ael-bin>
* AEL//bashlib - <https://github.com/alterEGO-Linux/ael-bashlib>
* GNU Tar - <https://www.gnu.org/software/tar/>
* `tar(1)` man page — <https://man.archlinux.org/man/core/tar/tar.1.en>
* GNU Gzip - <https://www.gnu.org/software/gzip/>
* `gunzip(1)` man page — <https://man.archlinux.org/man/core/gzip/gunzip.1.en>
* bzip2 - <https://www.sourceware.org/bzip2/docs.html>
* `bzip2` man page - <https://sourceware.org/bzip2/1.0.8/bzip2.txt>
* XZ Utils - <https://tukaani.org/xz/>
* `xz(1)` man page - <https://tukaani.org/xz/man/xz.1.html>
* `uncompress` ncompress project - <https://github.com/vapier/ncompress>
* `uncompress(1)` man page - <https://man.archlinux.org/man/extra/ncompress/uncompress.1.en>
* Info-ZIP - <https://infozip.sourceforge.net/>
* `unzip(1)` man page — <https://man.archlinux.org/man/unzip.1>
* RARLAB - <https://www.rarlab.com/>
* `unrar(1)` man page — <https://man-pages.org/unrar/1>
* 7-Zip - <https://www.7-zip.org/>
* `7z(1)` man page — <https://man.archlinux.org/man/extra/7zip/7z.1.en>
* GNU Cpio - <https://www.gnu.org/software/cpio/>
* `cpio(1)` man page - <https://man.archlinux.org/man/cpio.1.en>
