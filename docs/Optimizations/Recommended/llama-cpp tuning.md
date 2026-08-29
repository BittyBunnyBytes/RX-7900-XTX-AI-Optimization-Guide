This benchmark is using Qwen3.8-27B-Uncensored-IQ4_XS.gguf with the following hardware
64gb DDR4 RAM - 7900 XTX

Bench-marking settings
    -p 0 \
    -n 512 \
    -b 4096 \
    -ub 1024 \
    -t 7 \
    -ngl 999 \
    -fa on \
    -dev ROCm0 \
    -r 5

Pre-Tuning ROCm 7.2.4
| Model                          |      Size |  Params | Backend | NGL | Threads | Batch | UBatch | Flash Attention | Device | Test  |         Tokens/s |
| ------------------------------ | --------: | ------: | ------- | --: | ------: | ----: | -----: | --------------: | ------ | ----- | ---------------: |
| Qwen 3.5 27B IQ4_XS — 4.25 bpw | 14.25 GiB | 27.32 B | ROCm    | 999 |       7 |  4096 |   1024 |               1 | ROCm0  | tg512 | **38.25 ± 0.04** |

This looks pretty respectable already, but we can do better by installing stew675/llama-cpp-rdna-boosts
