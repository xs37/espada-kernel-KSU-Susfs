# Building Espada with GitHub Actions

The **Build Espada Kernel** workflow builds the public
[`atrejokm301/espada-kernel` `espada` branch](https://github.com/atrejokm301/espada-kernel/tree/espada).
It syncs the Android 16 / Linux 6.12 kernel manifest, overlays the selected Espada
source revision, and builds the ARM64 GKI distribution with Bazel/Kleaf from source.

## Run a build

1. Push this workflow to the repository where you want the run and enable GitHub Actions.
2. Open **Actions → Build Espada Kernel → Run workflow**.
3. Select exactly one **Root variant** and one **Mount option**.
4. Start the workflow and download the artifacts from the completed run.

Each dispatch is a single build; there is no all-variants matrix.

### Root variants

- **KernelSU** uses the KernelSU integration maintained in Espada.
- **KernelSU-Next** checks out the SUSFS-enabled `dev-susfs` kernel branch.
- **ReSukiSU** checks out its `main` kernel branch.

The selected implementation's manager APK must match the kernel you install. The
workflow does not build or package manager APKs.

### Mount options

- **Mountify** builds with OverlayFS support. Mountify itself is a userspace module;
  the workflow does not bundle it.
- **NoMount** integrates the selected NoMount revision and uploads a matching
  metamodule artifact.

## Artifacts and flashing

The kernel artifact contains the Kleaf distribution, build metadata, and checksums.
It is not an AnyKernel or device flashable ZIP. Espada's supported devices require
matching `boot.img` and `vendor_kernel_boot.img` images from the same build. If
either image is absent, do not flash the artifact as a complete kernel update.

Keep a stock boot/vendor-kernel-boot pair and a tested recovery path before
installing a custom build. Kernel bootability is device- and firmware-specific.
