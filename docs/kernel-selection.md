# Kernel selection

## Candidate
- Repository: https://github.com/jonas5/Allwinner-A733-kernel
- Kernel baseline: Linux 6.18
- Architecture: ARM64
- Board: Orange Pi 4 Pro (A733 / sun60iw2)

## Validation required
- Verify the exact 4 GB board device tree.
- Audit HAOS kernel requirements.
- Verify EROFS, Device Mapper, OverlayFS, cgroups and AppArmor.
- Preserve compatibility with the existing vendor U-Boot.
- Do not modify SPI flash.

## Status
Candidate identified. Not yet validated for HAOS.
