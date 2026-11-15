# Boot chain and technical constraints

## Existing board boot path

The current vendor installation boots through the board's U-Boot flow:

1. U-Boot reads `/boot/boot.cmd`.
2. The script loads `/boot/orangepiEnv.txt`.
3. It loads the kernel image, initramfs, and A733 device tree.
4. It applies configured overlays and starts the kernel with `bootm`.

The selected device tree is:

`allwinner/sun60i-a733-orangepi-4-pro.dtb`

The inspected installation does not expose an active UEFI environment. Therefore, the HAOS `generic_aarch64` target is not directly suitable: that target is built around GRUB and UEFI.

## HAOS integration model

HAOS is built with Buildroot. A board target normally defines:

- a Buildroot defconfig;
- board metadata and image-generation configuration;
- kernel configuration and device-tree selection;
- bootloader configuration and boot script;
- HAOS machine identifier and OS Agent board identifier;
- RAUC-compatible A/B partition layout.

A working target must integrate all of these pieces. Merely adding an EROFS option to the vendor kernel is not enough.

## A733 support status

A733 / sun60iw2 support is very new. Community U-Boot work has been published, but the board support and associated firmware chain must be validated for this exact 4 GB model before relying on it.

The current plan is to preserve the existing vendor boot path while developing the HAOS image integration. Replacing the bootloader is a separate, later decision and is not part of the first test cycle.

## Main blockers

1. Select a Linux kernel tree with verified A733 support and all HAOS kernel features.
2. Determine whether the existing vendor U-Boot can load the HAOS kernel, initramfs, device tree, and boot arguments reliably.
3. Define a board-specific HAOS image and partition layout.
4. Integrate Supervisor, OS Agent, Docker, AppArmor, and RAUC.
5. Test first boot and networking without touching SPI flash.
