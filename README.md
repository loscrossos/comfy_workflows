# ComfyUI Workflows

Ye olde honest repo... No complicated procedures..

only direct links to every single file you meed.

just download the files and save them where indicated and thats all!
(for the gguf loader plugin you can install it with comfyui manager).


### Update ComfyUI

First of all: update your ComfyUI. Only the latest version supports Qwen and wan22.

- on manual installation do a "git pull" on the comfyUI directory.
- on portable run the "ComfyUI_windows_portable\update\update_comfyui.bat"
- on Dekstop installation... not sure.

check this if in doubt: https://docs.comfy.org/installation/update_comfyui

### Overview Info

There are currently 2 main ways to use qwen on low vram: the safetensors models and the GGUF version.
For Qwen models. ComfyUI has official "Safetensors" FP8 workflows. On this repo you will find the guide for the GGUF versions. Why GGUF? by choosing quantizations sizes you can use the models on cards with less VRAM. Down to 6GB.
In my experience a good gguf has better quality on the same hardware. so i reccomend using that.

All Benchmarks on Torch 2.7.1, Sage-Attention 2.2. RTX 5060ti

## Flux Krea Dev

Krea has also a comfy workflow. here is a variation with GGUF instead.


Action  | link                                                                                                      | save to
---     |---                                                                                                        | ---
GETFILE | https://raw.githubusercontent.com/loscrossos/comfy_workflows/refs/heads/main/comfy_wf_flux1_krea_dev.json | ComfyUI/user/default/workflows/
GETFILE | https://huggingface.co/QuantStack/FLUX.1-Krea-dev-GGUF/resolve/main/flux1-krea-dev-Q8_0.gguf              | ComfyUI/models/unet
GETFILE | https://huggingface.co/comfyanonymous/flux_text_encoders/resolve/main/clip_l.safetensors                  | ComfyUI/models/text_encoders
GETFILE | https://huggingface.co/comfyanonymous/flux_text_encoders/resolve/main/t5xxl_fp8_e4m3fn.safetensors        | ComfyUI/models/text_encoders
GETFILE | https://huggingface.co/Comfy-Org/Lumina_Image_2.0_Repackaged/resolve/main/split_files/vae/ae.safetensors  | ComfyUI/models/vae
CLONEIT | https://github.com/city96/ComfyUI-GGUF                                                                    | ComfyUI/custom_nodes 
 
you can check all GGUFs here: https://huggingface.co/QuantStack/FLUX.1-Krea-dev-GGUF/


## Qwen Image


for qwen image i only have the is the oficial workflow for the "safetensors" version. its good enough.


Official Source:
- There is an official guide for the FP8 version here: https://docs.comfy.org/tutorials/image/qwen/qwen-image 
- on an updated comfy you can open "Browse Templates->Image->Qwen image"


in order to save time or for automation, here all the files you need. download all files below and run the model.

for 12GB VRAM:

Action  | link                                                                                                                                          | save to
---     |---                                                                                                                                            | ---
GETFILE | https://raw.githubusercontent.com/loscrossos/comfy_workflows/refs/heads/main/comfy_wf_qwen_image.json                                         | ComfyUI/user/default/workflows
GETFILE | https://huggingface.co/Comfy-Org/Qwen-Image_ComfyUI/resolve/main/split_files/diffusion_models/qwen_image_fp8_e4m3fn.safetensors               | ComfyUI/models/diffusion_models/
GETFILE | https://huggingface.co/Comfy-Org/Qwen-Image_ComfyUI/resolve/main/non_official/diffusion_models/qwen_image_distill_full_fp8_e4m3fn.safetensors | ComfyUI/models/diffusion_models/
GETFILE | https://huggingface.co/lightx2v/Qwen-Image-Lightning/resolve/main/Qwen-Image-Lightning-8steps-V1.1.safetensors                                | ComfyUI/models/loras
GETFILE | https://huggingface.co/Comfy-Org/Qwen-Image_ComfyUI/resolve/main/split_files/vae/qwen_image_vae.safetensors                                   | ComfyUI/models/vae
GETFILE | https://huggingface.co/Comfy-Org/Qwen-Image_ComfyUI/resolve/main/split_files/text_encoders/qwen_2.5_vl_7b_fp8_scaled.safetensors              | ComfyUI/models/text_encoders


The model used above is FP8, which works on 12GB VRAM already (16GB is better). if you have 24GB you can load the bf16 model from: https://huggingface.co/Comfy-Org/Qwen-Image_ComfyUI/tree/main/split_files/diffusion_models

if you need gguf models you can find them here: https://huggingface.co/QuantStack/Qwen-Image-Distill-GGUF/tree/main


### Benchmark
GGUF Q4_K_M, Resolution: 1328x1328, Sampler: 25 Steps
- sage-attention: 219s
- Pytorch Attention: 245s







## Qwen Edit

this workflow accepts safetensors or GGUF. 

basically both workflows share all models but the main mode.the only difference is the model loader (safetensor loader or gguf loader)
here i present tha workflow that accepts both but i only put the links online for the gguf, since its more efficient.
If you want to use safetensors just download the model from the official comfyui Huggingface site. I do not reccomend it. gguf is better.

Action  | link                                                                                                                              | save to
---     |---                                                                                                                                | ---
GETFILE | https://raw.githubusercontent.com/loscrossos/comfy_workflows/refs/heads/main/comfy_wf_qwen_edit_safetensorGGUF.json               |ComfyUI/user/default/workflows
GETFILE | https://huggingface.co/QuantStack/Qwen-Image-Edit-GGUF/resolve/main/Qwen_Image_Edit-Q6_K.gguf                                     |ComfyUI/models/unet
GETFILE | https://huggingface.co/lightx2v/Qwen-Image-Lightning/resolve/main/Qwen-Image-Lightning-8steps-V1.1.safetensors                    |ComfyUI/models/loras
GETFILE | https://huggingface.co/Comfy-Org/Qwen-Image_ComfyUI/resolve/main/split_files/text_encoders/qwen_2.5_vl_7b_fp8_scaled.safetensors  |ComfyUI/models/text_encoders
GETFILE | https://huggingface.co/Comfy-Org/Qwen-Image_ComfyUI/resolve/main/split_files/vae/qwen_image_vae.safetensors  	                    |ComfyUI/models/vae  
CLONEIT | https://github.com/city96/ComfyUI-GGUF                                                                                            |ComfyUI/custom_nodes 
 

### Benchmark

1024x1024, 8steps. Q6_K
- sage-attention:   84s. 7.2s/it
- Pytorch Attention: 109s. 11.4s/it



## WAN2.2 AIO (uncensored)

AIO comes as uncensored. This model was made by someone named Phr00t. 
You can switch between Text2Video and Image2Video by switching the model to be loaded.

Action  | link                                                                                                                              | save to
---     |---                                                                                                                                | ---
GETFILE |https://raw.githubusercontent.com/loscrossos/comfy_workflows/refs/heads/main/comfy_wf_wan2.2-ti2v-aio_uncensored.json              | ComfyUI/user/default/workflows
GETFILE |https://huggingface.co/Phr00t/WAN2.2-14B-Rapid-AllInOne/resolve/main/v8/wan2.2-i2v-rapid-aio-v8.safetensors                        | ComfyUI/models/checkpoints
GETFILE |https://huggingface.co/Phr00t/WAN2.2-14B-Rapid-AllInOne/resolve/main/v8/wan2.2-t2v-rapid-aio-v8.1.safetensors                      | ComfyUI/models/checkpoints
GETFILE |https://huggingface.co/Comfy-Org/Wan_2.1_ComfyUI_repackaged/resolve/main/split_files/clip_vision/clip_vision_h.safetensors         | ComfyUI/models/clip_vision
CLONEIT |https://github.com/city96/ComfyUI-GGUF                                                                                             | ComfyUI/custom_nodes


### Benchmark
640x640, 4Steps, length: 81

**Text2Video Generation** (less time is better):
- sage-attention: 145s 24s/it
- Pytorch Attention: 191s 36s/it

**Image2Video Generation** (less time is better)
- sage-attention: 175s 32s/it
- Pytorch Attention: 220s  45s/it