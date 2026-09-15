# AlterEGO Linux Documentation

Welcome to the centralized documentation for AlterEGO Linux.

This documentation describes the AEL environment, its applications, command-line tools, desktop components, shared conventions and development plans.

## Start here

New to AlterEGO Linux?

* [AlterEGO Linux overview](getting-started/overview.md)
* [Installation](getting-started/installation.md)
* [Directory layout](getting-started/directory-layout.md)
* [Configuration](getting-started/configuration.md)

## Components

### Applications

* [AEL//Colors](components/ael-colors/index.md) — Palette management and color utilities
* [AEL//Fuzz](components/ael-fuzz/index.md) — Configurable fuzzy finder and selection engine
* [AEL//Notifications](components/ael-notifications/index.md) — Desktop notifications, confirmations and progress reporting

### Desktop

* [AEL//Bar](components/ael-bar/index.md) — Quickshell desktop bar and applets
* [AEL//Carousel](components/ael-carousel/index.md) — Graphical application carousel
* [AEL//Architect](components/ael-architect/index.md) — AEL desktop management interface
* [AEL//Cyberdeck](components/ael-cyberdeck/index.md) — SDDM login theme

### Command-line tools

* [AEL//Bin](components/ael-bin/index.md) — Collection of small command-line utilities
* [AEL//Bin command reference](components/ael-bin/commands/index.md)

### Shared resources

* [AEL//Files](components/ael-files/index.md) — Shared assets, templates and static data

## Architecture

Learn how AEL components work together:

* [Architecture overview](architecture/overview.md)
* [AEL environment and `AEL_HOME`](architecture/ael-home.md)
* [Configuration paths](architecture/configuration-paths.md)
* [Shared appearance system](architecture/appearance-system.md)
* [Notifications and confirmations](architecture/notifications.md)
* [Component integration](architecture/component-integration.md)

## Guides

Task-oriented instructions:

* [Create an AEL application](guides/creating-an-ael-application.md)
* [Create an AEL//Bin command](guides/creating-an-ael-bin-command.md)
* [Publish a release](guides/publishing-a-release.md)
* [Write AEL documentation](guides/documentation-guidelines.md)

## Reference

Machine-readable catalogs and technical references:

* [Components](reference/components.toml)
* [Commands](reference/commands.toml)
* [Applications](reference/applications.toml)
* [Keybindings](reference/keybindings.toml)
* [Configuration paths](reference/paths.md)

Structured reference files are intended for both people and AEL applications. Their formats are defined under [`schemas/`](schemas/).

## Project decisions

Important architectural choices are recorded in the [decision log](decisions/README.md).

These records explain why major decisions were made, including:

* Centralizing AEL documentation
* Separating AEL//Bin from AEL//Files
* Selecting standard configuration paths
* Managing generated repository README files
* Separating human-readable documentation from structured reference data

## Documentation status

AEL//Documentation is being built progressively as existing documentation is migrated from component repositories and the former `ael-files` structure.

During this transition, some links or sections may not yet be available. Existing documentation should only be removed from its original location after its replacement has been reviewed and committed here.

## Source code

The documentation source is maintained in the `ael-documentation` Git repository.

