This benchmark is using Qwen3.8-27B-Uncensored-IQ4_XS.gguf with the following hardware
64gb DDR4 RAM - 7900 XTX

Settings I used
--gpu-layers 999999 \
--ctx-size 64000 \
--parallel 1 \
--batch-size 4096 \
--ubatch-size 1024 \
--threads 7 \
--flash-attn on \
--reasoning-preserve \
--kv-offload

For reference when I started running the same model with the same settings on LMStudio with a ROCm 7.14 back-end I got roughly 49tk/s. 
