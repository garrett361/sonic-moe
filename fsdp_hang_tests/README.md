Minimal repro of FSDP hangs on torch nightly. Seems to be a race condition, as I cannot reproduce
the hangs with CUDA_LAUNCH_BLOCKING=1. Maybe user error/package issues?

Tested on:

```
❯ nvidia-smi
Wed Mar 25 18:39:26 2026
+-----------------------------------------------------------------------------------------+
| NVIDIA-SMI 570.86.10              Driver Version: 570.86.10      CUDA Version: 12.8     |
|-----------------------------------------+------------------------+----------------------+
| GPU  Name                 Persistence-M | Bus-Id          Disp.A | Volatile Uncorr. ECC |
| Fan  Temp   Perf          Pwr:Usage/Cap |           Memory-Usage | GPU-Util  Compute M. |
|                                         |                        |               MIG M. |
|=========================================+========================+======================|
|   0  NVIDIA H100 80GB HBM3          On  |   00000000:3B:00.0 Off |                    0 |
| N/A   34C    P0            117W /  700W |    5720MiB /  81559MiB |      0%   E. Process |
|                                         |                        |             Disabled |
+-----------------------------------------+------------------------+----------------------+
|   1  NVIDIA H100 80GB HBM3          On  |   00000000:4C:00.0 Off |                    0 |
| N/A   33C    P0            125W /  700W |    5720MiB /  81559MiB |      0%   E. Process |
|                                         |                        |             Disabled |
+-----------------------------------------+------------------------+----------------------+
|   2  NVIDIA H100 80GB HBM3          On  |   00000000:5D:00.0 Off |                    0 |
| N/A   32C    P0             70W /  700W |       4MiB /  81559MiB |      0%   E. Process |
|                                         |                        |             Disabled |
+-----------------------------------------+------------------------+----------------------+
|   3  NVIDIA H100 80GB HBM3          On  |   00000000:9B:00.0 Off |                    0 |
| N/A   42C    P0             71W /  700W |       4MiB /  81559MiB |      0%   E. Process |
|                                         |                        |             Disabled |
+-----------------------------------------+------------------------+----------------------+

```

Python package versions listed in `sonic_hang_min.py`.
