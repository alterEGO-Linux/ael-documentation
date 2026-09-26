<!--
=============================================================================== 
INFO
===============================================================================
[/ael-documentation/guides/coding-conventions.md]

Author      : Pascal Malouin (https://github.com/alterEGO-Linux)
Created     : 2026-09-22 15:56:51 UTC
Updated     : 2026-09-25 15:23:12 UTC
Description : Coding conventions.
-------------------------------------------------------------------------------
-->

# Coding Conventions

Conventions are conventions, not requirements.

## Variables

|||
|:-|:-|
|`UPPERCASE`| environment/exported variables (`AEL_DATA`, `AEL_HOME`, etc.).|
|`_UPPERCASE`| script-level internal/private variables (`_DATA`).|
|`_lowercase`| short-lived variables (`_x`).|

## Python

### Python dependencies

Python dependencies belong to pyproject.toml and are installed into the 
application's venv.

This avoids relying on a possible system wide installation (ex. python-rich) 
and allows future compatibility on other environment than AEL ecosystem.
