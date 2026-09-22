<!--
=============================================================================== 
INFO
===============================================================================
[/ael-documentation/components/ael-bin/commands/dicom-tag.md]

Author      : Pascal Malouin (https://github.com/alterEGO-Linux)
Created     : 2026-09-21 11:40:58 UTC
Updated     : 2026-09-21 11:40:58 UTC
Description : dicom-tag.
-------------------------------------------------------------------------------
-->

# dicom-tag

Provides an interactive DICOM tag reference using `ael-fuzz`.

```bash
dicom-tag
```

Searches a built-in database of DICOM tags by tag number or attribute name, making it easy to quickly look up identifiers such as `PatientID`, `StudyInstanceUID`, or `Modality`.

## Requirements

* AEL//Bash library (`~/.ael/lib/bash/`).
* `ael-fuzz`

## To Do List

* Make AEL//Bash library path flexible and configurable.
