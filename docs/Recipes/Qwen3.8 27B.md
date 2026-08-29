This benchmark is using Qwen3.8-27B-Uncensored-IQ4_XS.gguf with the following hardware 64gb DDR4 RAM - 7900 XTX

TL;DR : Run with these settings for best results
 * (Install the RDNA Boost Scripts)
 * Flash Attention On
 * Use literally any ROCm version 7.2.4 - 10.0.0

# Batch Sizes

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
