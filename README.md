# Home Assistant OS for Orange Pi 4 Pro

Experimental, community-maintained porting project for the **Orange Pi 4 Pro (Allwinner A733 / sun60iw2, 4 GB RAM)**.

The goal is a native Home Assistant OS image with Supervisor, Apps, and the standard HAOS update architecture. This is **not** a Debian + Home Assistant Container installation.

> Status: early hardware bring-up and port design. No bootable HAOS image exists yet. The board is not an officially supported Home Assistant OS target.

## Current direction

- Target: Orange Pi 4 Pro, 4 GB.
- Boot path: the board's existing vendor U-Boot flow, not Generic AArch64 UEFI.
- OS build system: upstream Home Assistant OS / Buildroot.
- Kernel: evaluate the A733-capable Linux tree and upstream support before selecting a kernel baseline.
- Image layout, Supervisor integration, and RAUC A/B updates must follow HAOS conventions.

## Important safety boundary

The board contains SPI flash. The initial development and test plan avoids writing to SPI flash. Early boot tests should use removable media and preserve the existing boot path.

## Repository map

- [Hardware baseline](docs/hardware-baseline.md)
- [Boot chain and constraints](docs/boot-chain.md)
- [Porting roadmap](docs/roadmap.md)

## Upstream references

- [Home Assistant OS source](https://github.com/home-assistant/operating-system)
- [HAOS architecture and source layout](https://contributors.home-assistant.io/os/operating-system/)
- [HAOS build guide](https://contributors.home-assistant.io/os/operating-system/build/)
- [Supported HAOS boards](https://contributors.home-assistant.io/os/operating-system/boards/)

## Disclaimer

This project is experimental and is not affiliated with or endorsed by Home Assistant or Xunlong. A successful build does not imply that it will boot or that all board peripherals work.
