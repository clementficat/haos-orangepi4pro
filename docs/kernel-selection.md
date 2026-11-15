# Kernel selection

## Selected candidate
- Repository: https://github.com/jonas5/orangepi-4pro-kernel
- Kernel: Linux 7.1.5
- Architecture: ARM64
- SoC: Allwinner A733 / sun60iw2
- Board: Orange Pi 4 Pro 4 GB
- Device tree: sun60i-a733-orangepi-4-pro.dtb
- Kernel defconfig: orangepi_4pro_defconfig

## Validation required
- Audit HAOS kernel requirements.
- Verify EROFS, Device Mapper, OverlayFS and AppArmor.
- Validate boot through the existing U-Boot.
- Preserve the SPI flash.

## Status
Candidate identified. HAOS compatibility not yet validated.
