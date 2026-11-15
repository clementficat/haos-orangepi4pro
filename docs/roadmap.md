# Porting roadmap

## Phase 0: Hardware baseline
- [x] Identify the exact board and SoC.
- [x] Record the existing vendor boot flow and device tree.
- [x] Confirm Ethernet, SSH, microSD, and USB storage on the existing Debian image.
- [x] Confirm that the current vendor kernel is not a ready-made HAOS kernel.
- [x] Establish a no-SPI-write rule for early development.

## Phase 1: Kernel and boot feasibility
- [ ] Choose a kernel source and pinned revision for A733.
- [ ] Confirm the device tree for the 4 GB Orange Pi 4 Pro.
- [ ] Produce a kernel config containing the HAOS requirements.
- [ ] Validate kernel + initramfs + DTB loading through the existing U-Boot.
- [ ] Verify Ethernet and USB from that kernel.

## Phase 2: HAOS board target
- [ ] Add `orangepi4pro_defconfig`.
- [ ] Add board metadata, boot assets, and image-generation configuration.
- [ ] Add board-specific kernel and bootloader integration.
- [ ] Define the HAOS machine and OS Agent identifiers.
- [ ] Generate a first complete image in CI.

## Phase 3: First boot
- [ ] Boot from a spare removable medium.
- [ ] Confirm partition discovery and persistent data storage.
- [ ] Confirm NetworkManager and Ethernet.
- [ ] Confirm Docker and Supervisor startup.
- [ ] Confirm Apps support.

## Phase 4: Reliability and updates
- [ ] Validate RAUC A/B updates and rollback.
- [ ] Test reboot and power-loss recovery.
- [ ] Document recovery and installation steps.
- [ ] Publish checksums and known limitations.

## Current milestone

**Phase 0 is documented. Phase 1 is next.** No image should be flashed to the working system until a separate boot test and recovery method are established.
