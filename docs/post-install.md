# After the Espada build

1. Download the kernel artifact from the successful **Build Espada Kernel** run.
2. Confirm the artifact has both `boot.img` and `vendor_kernel_boot.img`. These
   images must be installed as a matching pair from the same build.
3. Install the manager corresponding to the selected root implementation.
4. Install and configure any optional root-hiding or module-mounting userspace
   modules separately. Mountify is not bundled. For a NoMount build, use the
   matching NoMount metamodule artifact from the same workflow run.

The workflow does not package a device flashable ZIP or a manager APK. Keep the
stock image pair and recovery method available before flashing.
