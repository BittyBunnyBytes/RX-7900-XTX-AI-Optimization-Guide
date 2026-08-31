## So you want to run LTX 2.5 on your 7900 XTX
> Note : This was ran with 64GB DDR4 Ram and one 7900 XTX with 24 GB of vram

When I first bought my 7900 XTX using LTX 2.5 ate all my system resources and generated bad quality footage. Now I am able to generate 5 second 1024x704 video in roughly 1m 49s with not much jump in time when generating at higher resolution or longer duration.

Assuming you're like me and aren't a comfyui god I suggest using this workflow
https://civitai.com/models/2852749/ltx-25-int8-allinone-speed-quality-low-vram

**Now, lets go over the settings I am using for this workflow.**

**Models**
* LTX 2.5 Video & Audio Vae at bf16
* Gemma 4 12B Uncensored Heretic LTX2.5 int18 convrot
* LTX 2.5 Latent Spatial Upscaler x2 bf16
* LTX 2.5 22b distilled transformer comfy int8 convrot (this is the actual model)

**Backend**
ROCm 7.14 Pytorch XXX

**ComfyUI Startup Arguments**
--disable-pinned-memory --cache-none --enable-dynamic-vram --disable-smart-memory --fast-disk --disable-async-offload --disable-triton-backend --preview-method none --disable-metadata --use-split-cross-attention 
