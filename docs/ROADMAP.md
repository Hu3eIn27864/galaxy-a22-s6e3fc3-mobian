# S6E3FC3 DRM Panel Driver Roadmap

Target: Samsung Galaxy A22 LTE SM-A225F, S6E3FC3 MIPI-DSI panel. Current status is source research only; no standalone DRM panel driver build or hardware bring-up is confirmed.

Estimates assume one developer familiar with Linux DRM/MIPI-DSI and access to the exact device.

## M0 — Hardware and source specification (1–2 weeks)
- [ ] Record exact panel revision and firmware/device-tree provenance.
- [ ] Separate verified board wiring/power resources from vendor-framework behavior.
- [ ] Document command sequences with provenance and licensing review.
**Exit:** reviewable specification with unresolved facts clearly marked.

## M1 — Minimal DRM panel driver (3–6 weeks)
- [ ] Implement standard DRM panel and MIPI-DSI integration.
- [ ] Use regulator, GPIO, backlight and reset resources from device tree.
- [ ] Add panel prepare/enable/disable/unprepare lifecycle.
- [ ] Build against the intended Mobian kernel tree/configuration.
**Exit:** clean kernel build and static review; no display success claim yet.

## M2 — Device-tree integration (2–4 weeks)
- [ ] Add panel node and endpoint graph for SM-A225F.
- [ ] Validate DSI lane count, pixel format, timings and reset/power sequencing.
- [ ] Run applicable dt-schema checks.
**Exit:** device-tree validation passes.

## M3 — Hardware bring-up (2–8 weeks)
- [ ] Test panel initialization and first frame.
- [ ] Validate brightness/backlight and display-off/sleep.
- [ ] Test suspend/resume and repeated enable/disable.
- [ ] Capture logs and document panel revisions.
**Exit:** reproducible display test on the exact device.

## M4 — Upstream quality (2–4 weeks)
- [ ] Add error handling and resource cleanup.
- [ ] Review bindings and coding style.
- [ ] Submit patches for review and document limitations.
**Exit:** review-ready patch series.

Dynamic refresh rates and calibration refinements are deferred until basic display operation is stable.
