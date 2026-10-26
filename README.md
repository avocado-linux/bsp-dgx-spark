# bsp-dgx-spark

> Board support for the NVIDIA DGX Spark (GB10) on the generic `arm64-uefi-v9` target.

The Spark has no machine of its own: it builds on `arm64-uefi-v9`, the Armv9-A
UEFI machine in `meta-avocado-arm64`, and this extension carries everything
board-specific: the GB10 iGPU driver stack, ConnectX-7 Ethernet and RDMA (with
unlimited locked memory for NCCL/UCX), RTL8127A and MT7925 firmware, and a unit
that hands CPU performance selection to the hardware (CPPC autonomous mode), as
DGX OS does.

Before first boot, update the Spark's firmware from DGX OS (`fwupdmgr update`;
the factory firmware boots only DGX OS) and disable Secure Boot in UEFI setup.

## Using this extension

`bsp-dgx-spark` is an [Avocado](https://avocadolinux.org) extension — a reusable fragment of
build- and runtime-configuration that you compose into your own Avocado project. To use it,
declare it as a package-sourced extension in your `avocado.yaml` and add it to a runtime:

```yaml
extensions:
  avocado-bsp-dgx-spark:
    source:
      type: package
      version: "*"        # or pin an exact version

runtimes:
  my-runtime:
    extensions:
      - avocado-bsp-dgx-spark
```

Then install and build:

```sh
avocado install   # fetches + installs the SDK, extensions and runtime deps from your config
avocado build     # builds the SDK compile steps, extensions and runtime images
```

`avocado install` pulls the extension from your target's package feed and merges its
config into your project; `avocado build` then produces the runtime.
