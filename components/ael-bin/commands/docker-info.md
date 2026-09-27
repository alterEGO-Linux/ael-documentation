<!--
===============================================================================
INFO
===============================================================================
[/ael-documentation/components/ael-bin/commands/docker-info.md]

Author      : Pascal Malouin (https://github.com/alterEGO-Linux)
Created     : 2026-09-27 14:27:00 UTC
Updated     : 2026-09-27 14:27:00 UTC
Description : Docker status helper.
-------------------------------------------------------------------------------
-->

# docker-info

Provides a quick overview of Docker containers and images using formatted terminal tables.

```bash
docker-info --containers
```

The command uses the Docker CLI to retrieve information and presents the results using Rich tables.

If `docker.service` is not active on a Linux system using systemd, `docker-info` attempts to restart the service automatically before querying Docker.

## Usage

Show all Docker containers, including stopped containers:

```bash
docker-info --containers
```

The container table displays:

* Container ID
* Name
* Status
* Image
* Docker networks
* IP address

Show locally available Docker images:

```bash
docker-info --images
```

The image table displays:

* Image ID
* Repository
* Tag
* Created
* Size

Show both containers and images:

```bash
docker-info --all
```

Exactly one of `--containers`, `--images`, or `--all` must be specified.

## Examples

Inspect the current Docker environment:

```bash
docker-info --all
```

Check container status and network information:

```bash
docker-info --containers
```

Check which Docker images are installed:

```bash
docker-info --images
```

## Docker Service

On Linux systems using systemd, `docker-info` checks the state of `docker.service` before retrieving Docker information.

If the service is not active, it attempts:

```bash
systemctl restart docker
```

The service state is then checked again before continuing.

On systems without systemd, this step is skipped.

## Requirements

* Python 3
* Docker CLI
* Docker daemon
* `rich`
* `systemctl` on Linux when automatic Docker service management is desired

Install the Python dependency with:

```bash
pip install rich
```

On Arch Linux or AEL ecosystem, Rich can also be installed system-wide with:

```bash
sudo pacman -S python-rich
```

## Resources

* [AEL//Documentation](https://github.com/alterEGO-Linux/ael-documentation)
* [Docker CLI documentation](https://docs.docker.com/reference/cli/docker/)
* [Rich documentation](https://rich.readthedocs.io/)
