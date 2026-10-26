# Changelog

All notable changes to avocado-bsp-dgx-spark are documented in this file.
The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [0.1.4]

### Added
- Wi-Fi and Bluetooth userspace: wpa-supplicant, iw, bluez5 (bluetooth.service
  enabled).
- HDMI audio: snd-hda-acpi with the HDMI and NVIDIA HDMI codecs, and aplay.

## [0.1.3]

### Added
- fwupd, so the Spark's SoC, EC and USB-C PD firmware update from LVFS under
  Avocado (capsule-on-disk), without DGX OS.

## [0.1.2]

### Added
- The rest of the RDMA stack rdma-core loads at boot: ib_ipoib, ib_umad,
  ib_iser and rpcrdma.

## [0.1.1]

### Added
- Targets the generic `arm64-uefi-v9` machine (meta-avocado-arm64); the Spark
  no longer has a machine of its own.
- ConnectX-7 RDMA: mlx5_ib, ib_uverbs, rdma_ucm and rdma-core, with unlimited
  locked memory for NCCL/UCX (systemd DefaultLimitMEMLOCK and PAM limits).
- `dgx-spark-cppc-autonomous.service`: CPPC autonomous performance selection
  with EPP 0, as DGX OS boots.
- wireless-regdb-static for the MT7925.

## [0.1.0]

### Added
- Initial release: Board support for the NVIDIA DGX Spark (GB10).
- CI via the shared `avocado-linux/actions` reusable workflows: PR build check
  (`test.yml`) and tag-driven package + publish to the Avocado feed (`release.yml`).
