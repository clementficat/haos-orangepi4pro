# Hardware baseline

This file records observations from the 4 GB Orange Pi 4 Pro used for development. It is a working baseline, not a claim that every hardware block is supported by mainline Linux.

## Board

| Item | Observed value |
|---|---|
| Board | Orange Pi 4 Pro |
| SoC | Allwinner A733 / sun60iw2 |
| RAM | 4 GB |
| Architecture | AArch64 |
| Current OS used for inspection | Debian 12 Bookworm |
| Current vendor kernel | 5.15.147-sun60iw2 |
| Bootloader | Vendor U-Boot 2018.07 |
| Device tree | allwinner/sun60i-a733-orangepi-4-pro.dtb |
| Root device during inspection | microSD, /dev/mmcblk1p1 |
| SPI flash | /dev/mtdblock0, 16 MB |

## Known working on the existing Debian installation

- Ethernet networking and SSH.
- USB mass storage.
- microSD boot.
- Vendor device tree is present under /boot.

These observations apply to the existing vendor Debian image only. They do not prove that the same devices work with a different kernel or bootloader.

## Kernel configuration observations

The inspected vendor kernel has several useful options enabled, including ARM64, SquashFS, OverlayFS, EXT4, loop devices, cgroups, initramfs, devtmpfs, and USB storage.

The following required HAOS-related capabilities were not confirmed in this kernel inspection:

- EROFS filesystem support was explicitly disabled.
- Device Mapper support was not found in the inspected configuration.
- EFI support was not enabled; /sys/firmware/efi was absent.

This means the vendor kernel is not a drop-in HAOS kernel. A dedicated kernel configuration and boot integration are required.

## Storage layout observed during inspection

The removable USB test drive contained the standard HAOS Raspberry Pi image partitions:

1. hassos-boot
2. hassos-kernel0
3. hassos-system0
4. hassos-kernel1
5. hassos-system1
6. hassos-bootstate
7. hassos-overlay
8. hassos-data

This was only used to inspect the HAOS image layout. It is not a compatible Orange Pi 4 Pro image.

## Safety constraints

- Do not write to the SPI flash during initial porting.
- Do not overwrite the working Debian microSD until a separate, independently bootable test medium and recovery path are available.
- Prefer USB or a spare microSD for experiments.
- Do not assume a Raspberry Pi HAOS image can boot on this board.
