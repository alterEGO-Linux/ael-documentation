# AEL//Documentation

Centralized documentation and machine-readable reference data for the AlterEGO Linux ecosystem.

AEL//Documentation is the primary source for:

* Component documentation
* Installation and configuration guides
* Command references
* Development notes
* Architecture decisions
* Release documentation
* Shared TOML and JSON catalogs

The goal is to provide one organized place for documenting AlterEGO Linux instead of maintaining overlapping README files across numerous repositories and directories.

## Documentation

Start with the [documentation home page](index.md).

Important sections:

* [Getting started](getting-started/overview.md)
* [Components](components/index.md)
* [Architecture](architecture/overview.md)
* [Guides](guides/index.md)
* [Reference data](reference/README.md)
* [Development decisions](decisions/README.md)

## Source of truth

Documentation maintained in this repository is considered the primary source for the AlterEGO Linux ecosystem.

Individual component repositories may still contain a concise `README.md` for:

* A short project description
* Basic installation instructions
* Essential usage examples
* A link to the complete documentation

When a repository README is generated from this project, changes should be made here first and then synchronized with the corresponding repository.

Documentation that must remain coupled to a specific source revision may stay inside the component repository.

## Machine-readable reference data

In addition to Markdown documentation, this repository contains structured TOML and JSON files that can be consumed by AEL applications.

Examples include:

* Application catalogs
* Command catalogs
* Component metadata
* Keybindings
* Configuration paths
* Dependencies

These files may be used by tools such as AEL//Fuzz and by the future AEL documentation interface.

## Repository structure

```text
ael-documentation/
├── architecture/       System architecture and shared conventions
├── components/         Documentation for individual AEL components
├── decisions/          Important architectural and project decisions
├── getting-started/    Introductory and installation documentation
├── guides/             Task-oriented guides
├── reference/          Machine-readable catalogs and reference material
├── schemas/            Schemas for validating structured data
├── templates/          Documentation templates
└── tools/              Documentation maintenance utilities
```

## Contributing

Before adding or changing documentation, read the [documentation guidelines](guides/documentation-guidelines.md).

General principles:

1. Maintain one authoritative source for each subject.
2. Link to existing information instead of duplicating it.
3. Keep instructions close to the component they describe.
4. Separate current documentation from historical release notes.
5. Validate machine-readable files before committing them.
6. Clearly identify generated files.

## Project

AEL//Documentation is part of the AlterEGO Linux project.

