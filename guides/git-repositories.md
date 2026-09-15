<!--
=============================================================================== 
INFO
===============================================================================
 [/ael-documentation/guides/git-repositories.md]

 Author      : Pascal Malouin (https://github.com/alterEGO-Linux)
 Created     : 2026-09-15 12:13:18 UTC
 Updated     : 2026-09-15 12:13:18 UTC
 Description : Guide: Git repository.
-------------------------------------------------------------------------------
-->

# Guide: Git repositories

This guide describes how to create and manage Git repositories for AlterEGO
Linux components.

## Initialization

First, create a repository on GitHub using the following naming convention:

* Repository ame: `ael-<component>`
* Component name: `AEL//<Component>`

Add a consise description explaining the component's purpose.

Do not add a license, `README.md` or a `.gitignore` when creating the GitHub 
repository. Those files should be created in the local development repository.

Create the local project directory, initialize the repository, and push the 
initial commit:

```bash
mkdir ael-<component>
cd ael-<component>
git init -b main
git add <files>
git commit -m "Initial commit AEL//<Component>"
git remote add origin git@github.com:alterEGO-Linux/ael-<component>.git
git remote -v
git push -u origin main
```
