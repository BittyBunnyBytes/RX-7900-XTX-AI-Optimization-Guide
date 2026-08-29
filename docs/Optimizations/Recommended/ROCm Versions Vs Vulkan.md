Note. This is an addendum to https://github.com/BittyBunnyBytes/RX-7900-XTX-AI-Optimization-Guide/blob/main/docs/Optimizations/Recommended/llama-cpp%20tuning.md and is running llama.cpp with RDNA boosts.

| Model                          |      Size |  Params | Backend    | NGL | Threads | Batch | UBatch | Flash Attention | Device | Test   |            Tokens/s |
| ------------------------------ | --------: | ------: | ---------- | --: | ------: | ----: | -----: | --------------: | ------ | ------ | ------------------: |
| Qwen 3.5 27B IQ4_XS — 4.25 bpw | 14.25 GiB | 27.32 B | ROCm 7.2.4 | 999 |       7 |  4096 |   1024 |               1 | ROCm0  | pp4096 | **1082.05 ± 2.59** |
| Qwen 3.5 27B IQ4_XS — 4.25 bpw | 14.25 GiB | 27.32 B | ROCm 7.2.4 | 999 |       7 |  4096 |   1024 |               1 | ROCm0  | tg512  |   **40.86 ± 0.19** |
| Qwen 3.5 27B IQ4_XS — 4.25 bpw | 14.25 GiB | 27.32 B | ROCm 7.14  | 999 |       7 |  4096 |   1024 |               1 | ROCm0  | pp4096 | **1103.78 ± 1.70** |
| Qwen 3.5 27B IQ4_XS — 4.25 bpw | 14.25 GiB | 27.32 B | ROCm 7.14  | 999 |       7 |  4096 |   1024 |               1 | ROCm0  | tg512  |   **40.00 ± 0.06** |
| Qwen 3.5 27B IQ4_XS — 4.25 bpw | 14.25 GiB | 27.32 B | ROCm 10.0  | 999 |       7 |  4096 |   1024 |               1 | ROCm0  | pp4096 | **1112.00 ± 3.46** |
| Qwen 3.5 27B IQ4_XS — 4.25 bpw | 14.25 GiB | 27.32 B | ROCm 10.0  | 999 |       7 |  4096 |   1024 |               1 | ROCm0  | tg512  |   **40.79 ± 0.09** |
