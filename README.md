# Samsung Galaxy A22 (SM-A225F) — S6E3FC3 panel for Mobian

**Status: early research. No working standalone DRM panel driver is available yet.**

This project investigates bringing up the Samsung S6E3FC3 display on the Galaxy A22 LTE (SM-A225F) for a Linux DRM/KMS-based mobile Linux system such as Mobian.

## Hardware notes

- Device: Samsung Galaxy A22 LTE, SM-A225F
- SoC/platform: MediaTek MT6769T
- Panel: Samsung S6E3FC3
- Resolution: 720 × 1600
- DSI: four lanes, command mode, RGB888
- Physical dimensions in vendor device tree: approximately 67 × 148 mm

Do not confuse this device with the Galaxy A22 5G (SM-A226B); it has a different SoC and display configuration.

## Research completed

Vendor-kernel research has identified panel initialization sequences for two vendor-selected revisions, sleep/display commands and delays, device-tree power/reset sequencing, display timing and DSI configuration.

A preliminary source file explored in the vendor kernel uses Samsung's SMCDSD framework. It is **not** a standalone upstream-style DRM panel driver and is not claimed to work with Mobian. No standalone driver build or hardware display test has been confirmed.

## Roadmap

See [docs/ROADMAP.md](docs/ROADMAP.md) for milestones and conditional estimates. The next goal is a minimal standard DRM/MIPI-DSI panel driver and a clean kernel build—not a ready-to-flash image.

## Safety and testing

This repository is not a ready-to-flash kernel, Mobian image or device port. Do not flash untested images. Keep a known-good stock boot image and recovery path. Record the exact SM-A225F firmware and panel revision in every test report.

## Licensing

The intended license for driver code derived from Samsung GPL-licensed kernel sources is GPL-2.0. Preserve original copyright and license notices. Documentation does not relicense Samsung source code.
