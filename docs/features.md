# Espada build options

Espada targets the Pixel 11 `spacecraft` family on Android 16 / Linux 6.12.

| Option | Workflow behavior |
|---|---|
| KernelSU | Uses the implementation in the Espada source branch. |
| KernelSU-Next | Replaces the in-tree root implementation with the SUSFS-enabled `dev-susfs` branch. |
| ReSukiSU | Replaces the in-tree root implementation with the `main` branch. |
| SUSFS | Enabled in the selected KernelSU-based build configuration. |
| OverlayFS / Mountify | OverlayFS is enabled in the kernel. Mountify must be installed separately. |
| NoMount | Integrates NoMount into the kernel and builds a matching metamodule artifact. |

The workflow selects only one root implementation and one mount option in each run.
