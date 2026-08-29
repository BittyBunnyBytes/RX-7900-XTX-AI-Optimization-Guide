This benchmark is using Qwen3.8-27B-Uncensored-IQ4_XS.gguf with the following hardware 64gb DDR4 RAM - 7900 XTX

TL;DR : Run with these settings for best results
 * (Install the RDNA Boost Scripts)
 * Flash Attention On
 * Use literally any ROCm version 7.2.4 - 10.0.0

# Batch Sizes

| Model                          |      Size | Backend   | Prompt | Batch | UBatch | Flash Attention | Device |          Tokens/s | Peak VRAM Used | Peak VRAM Free | Status                  |
| ------------------------------ | --------: | --------- | -----: | ----: | -----: | --------------: | ------ | ----------------: | -------------: | -------------: | ----------------------- |
| Qwen 3.5 27B IQ4_XS — 4.25 bpw | 14.25 GiB | ROCm 10.0 |   8192 |   512 |    512 |               1 | ROCm0  | **1022.66 ± 2.37** |      15.90 GiB |       8.08 GiB | Completed               |
| Qwen 3.5 27B IQ4_XS — 4.25 bpw | 14.25 GiB | ROCm 10.0 |   8192 |  1024 |   1024 |               1 | ROCm0  | **1071.26 ± 2.11** |      16.43 GiB |       7.56 GiB | Completed — fastest     |
| Qwen 3.5 27B IQ4_XS — 4.25 bpw | 14.25 GiB | ROCm 10.0 |   8192 |  2048 |   2048 |               1 | ROCm0  | **1063.00 ± 0.93** |      17.54 GiB |       6.44 GiB | Completed               |
| Qwen 3.5 27B IQ4_XS — 4.25 bpw | 14.25 GiB | ROCm 10.0 |   8192 |  3072 |   3072 |               1 | ROCm0  | **1058.44 ± 0.97** |      18.52 GiB |       5.46 GiB | Completed               |
| Qwen 3.5 27B IQ4_XS — 4.25 bpw | 14.25 GiB | ROCm 10.0 |   8192 |  4096 |   4096 |               1 | ROCm0  | **1035.77 ± 1.67** |      19.61 GiB |       4.38 GiB | Completed               |
| Qwen 3.5 27B IQ4_XS — 4.25 bpw | 14.25 GiB | ROCm 10.0 |   8192 |  5120 |   5120 |               1 | ROCm0  | **1031.23 ± 1.91** |      20.60 GiB |       3.38 GiB | Completed               |
| Qwen 3.5 27B IQ4_XS — 4.25 bpw | 14.25 GiB | ROCm 10.0 |   8192 |  6144 |   6144 |               1 | ROCm0  | **1019.91 ± 2.00** |      21.65 GiB |       2.34 GiB | Completed — last safe   |
| Qwen 3.5 27B IQ4_XS — 4.25 bpw | 14.25 GiB | ROCm 10.0 |   8192 |  7168 |   7168 |               1 | ROCm0  |                 — |      22.59 GiB |       1.39 GiB | Safety termination      |


# ROCm Versions (Using RDNA Boost) Vs Vulkan

| Model                          |      Size |  Params | Backend    | NGL | Threads | Batch | UBatch | Flash Attention | Device | Test   |            Tokens/s |
| ------------------------------ | --------: | ------: | ---------- | --: | ------: | ----: | -----: | --------------: | ------ | ------ | ------------------: |
| Qwen 3.5 27B IQ4_XS — 4.25 bpw | 14.25 GiB | 27.32 B | ROCm 7.2.4 | 999 |       7 |  4096 |   1024 |               1 | ROCm0  | pp4096 | **1082.05 ± 2.59** |
| Qwen 3.5 27B IQ4_XS — 4.25 bpw | 14.25 GiB | 27.32 B | ROCm 7.2.4 | 999 |       7 |  4096 |   1024 |               1 | ROCm0  | tg512  |   **40.86 ± 0.19** |
| Qwen 3.5 27B IQ4_XS — 4.25 bpw | 14.25 GiB | 27.32 B | ROCm 7.14  | 999 |       7 |  4096 |   1024 |               1 | ROCm0  | pp4096 | **1103.78 ± 1.70** |
| Qwen 3.5 27B IQ4_XS — 4.25 bpw | 14.25 GiB | 27.32 B | ROCm 7.14  | 999 |       7 |  4096 |   1024 |               1 | ROCm0  | tg512  |   **40.00 ± 0.06** |
| Qwen 3.5 27B IQ4_XS — 4.25 bpw | 14.25 GiB | 27.32 B | ROCm 10.0  | 999 |       7 |  4096 |   1024 |               1 | ROCm0  | pp4096 | **1112.00 ± 3.46** |
| Qwen 3.5 27B IQ4_XS — 4.25 bpw | 14.25 GiB | 27.32 B | ROCm 10.0  | 999 |       7 |  4096 |   1024 |               1 | ROCm0  | tg512  |   **40.79 ± 0.09** |
| Qwen 3.5 27B IQ4_XS — 4.25 bpw | 14.25 GiB | 27.32 B | Vulkan     | 999 |       7 |  4096 |   1024 |               1 | Vulkan0 | pp4096 |  **539.03 ± 4.18** |
| Qwen 3.5 27B IQ4_XS — 4.25 bpw | 14.25 GiB | 27.32 B | Vulkan     | 999 |       7 |  4096 |   1024 |               1 | Vulkan0 | tg512  |   **22.02 ± 0.04** |
