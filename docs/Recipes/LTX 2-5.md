## So you want to run LTX 2.5 on your 7900 XTX
> Note : This was ran with 64GB DDR4 Ram and one 7900 XTX with 24 GB of vram

There's a lot of hype over H3, but LTX 2.5 can be just as good especially at the speed it generates. If you run LTX2.5 out of the box however, it will look absolutely horrible and sound even worse. When I first bought my 7900 XTX using LTX 2.5 ate all my system resources and generated bad quality footage. Now I am able to generate 5 second 1024x704 video in roughly 1m 31s with not much jump in time when generating at higher resolution or longer duration. Let me be clear, when I say "run" I don't mean at low quality and resolution. If I wanted horrible quality I would've stayed on my 7800 xt.

## Now if you JUST wan't it to run here is what I use.

Assuming you're like me and aren't a comfyui god I suggest using this workflow
https://civitai.com/models/2852749/ltx-25-int8-allinone-speed-quality-low-vram

**Models**
* LTX 2.5 Video & Audio Vae at bf16
* Gemma 4 12B Uncensored Heretic LTX2.5 int18 convrot
* LTX 2.5 Latent Spatial Upscaler x2 bf16
* LTX 2.5 22b distilled transformer comfy int8 convrot (this is the actual model)

**Backend**
ROCm 7.14 Pytorch XXX

**ComfyUI Startup Arguments**
--disable-pinned-memory --cache-none --enable-dynamic-vram --disable-smart-memory --fast-disk --disable-async-offload --disable-triton-backend --preview-method none --disable-metadata --use-split-cross-attention 

## Field Notes
**Don't go over VRAM**
If you don't crash, you WILL get garbage gibberish audio and what looks like old film burning if you go over the VRAM you have. For some reason on this workflow if you don't generate using medium tiles at least once, you will ALWAYS go over VRAM when trying to use large tiles.

## Now why these settings and not the other ones?

### Attention Benchmark
> Workflow Settings : Large Tiles, 1024w 704h, 30 fps, 5 seconds, randomized seed

> Prompt: A realistic man faces the camera and says clearly: “I have absolutely no idea what I’m doing.” Natural expression, clear speech, accurate lip sync, stable camera, no extra voices.

| Method                          | Trial 1 | Trial 2 | Trial 3 | Trial 4 | Trial 5 | Average | Est. 15s |
| ------------------------------- | :-----: | :-----: | :-----: | :-----: | :-----: | :-----: | :------: |
| Split Cross Attention           | 1m 49s  | 1m 49s  | 1m 49s  | 1m 49s  | 1m 50s  | 1:49    | 5:28     |
| Flash Attention                 | 1m 31s  | 1m 31s  | 1m 31s  | 1m 31s  | 1m 30s  | 1:31    | 4:32     |
| Sage Attention                  | 1m 35s  | 1m 36s  | 1m 35s  | 1m 38s  | 1m 37s  | 1:36    | 4:49     |
| CK Attention (W/Triton Backend) | 1m 31s  | 1m 31s  | 1m 31s  | 1m 31s  | 1m 31s  | 1:31    | 4:33     |
| Pytorch Cross Attention         | 1m 46s  | 1m 46s  | 1m 46s  | 1m 47s  | 1m 45s  | 1:46    | 5:18     |
