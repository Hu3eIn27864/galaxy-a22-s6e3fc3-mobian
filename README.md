# Samsung Galaxy A22 (SM-A225F) — S6E3FC3 panel for Mobian

**Status: early work in progress. Not a working driver.**

This repository tracks the effort to bring up the Samsung Galaxy A22 LTE (SM-A225F) display on a Linux DRM/KMS-based mobile Linux system such as Mobian.

The target panel is the Samsung S6E3FC3, connected over MIPI-DSI.

## Device and display notes

The Samsung vendor device tree and panel driver examined so far describe:

- Device: Samsung Galaxy A22 LTE, SM-A225F
- SoC/platform: MediaTek MT6769T
- Panel: Samsung S6E3FC3
- Resolution: 720 × 1600
- DSI: four lanes, command mode, RGB888
- Physical dimensions in the vendor device tree: approximately 67 × 148 mm
- Panel reset and power sequencing are described by the device tree and should be reused through standard Linux resources rather than hard-coded GPIO numbers.

**Do not confuse this device with the Galaxy A22 5G (SM-A226B).** That is a different device and has a different SoC/display configuration.

## Current status

Research and reverse-engineering notes have been collected from the Samsung vendor kernel:

- Panel initialization command sequences for two vendor-selected panel revisions.
- Sleep-out, display-off and sleep-in commands and their delays.
- Device-tree power and reset action sequences.
- Vendor display timing and DSI configuration.
- The vendor framework's division of responsibilities for display-on and panel initialization.

A preliminary source file was created in the vendor kernel tree during exploration. It uses Samsung's SMCDSD framework and is **not** a standalone upstream-style DRM panel driver. It has not been validated as a Mobian driver and is not included here as a working implementation.

No successful standalone driver build, display bring-up, or hardware test is claimed at this stage.

## Roadmap

1. Finish documenting the original panel commands and board sequencing.
2. Implement a standalone Linux DRM panel driver using the standard MIPI-DSI and DRM panel APIs.
3. Add the appropriate device-tree description and bindings for the SM-A225F.
4. Build against the intended Mobian kernel configuration.
5. Test panel initialization, image output, backlight, suspend and resume on hardware.
6. Consider dynamic 60/90 Hz modes and vendor-calibrated brightness only after basic display operation works.

## Safety and testing

This is experimental kernel work. It is not a ready-to-flash kernel, Mobian image, or device port. Do not flash untested images or assume that the display will work. Keep a known-good stock boot image and recovery path.

## Contributions

Corrections to the hardware identification, vendor command sequences, device-tree data, and build/test reports are welcome. Please include the exact device model (SM-A225F) and distinguish verified hardware results from source-code analysis.

## License

The intended license for kernel-driver code derived from the Samsung GPL-licensed kernel sources is GPL-2.0. Any imported source files must retain their original copyright and license notices. This repository's initial documentation does not relicense Samsung source code.
