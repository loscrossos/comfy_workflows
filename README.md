# ComfyUI Workflows

Ye olde honest repo...

First of all: upadte your ComfyUI. Only the latest version supports Qwen and wan22.

- on manual installation do a "git pull" on the comfyUI directory.
- on portable run the "ComfyUI_windows_portable\update\update_comfyui.bat"
- on Dekstop installation... not sure.

check this if in doubt: https://docs.comfy.org/installation/update_comfyui

For Qwen ComfyUI has official FP8 versions. Here you will find the guide for the GGUF versions. Why GGUF? by choosing quantizations sizes you can use the models on cards with less VRAM. Down to 6GB.


All Benchmarks on Torch 2.7.1, Sage-Attention 2.2. RTX 5060ti

## Qwen Image

Official Source:

- There is an official guide for the FP8 version here: https://docs.comfy.org/tutorials/image/qwen/qwen-image 
- on an updated comfy you can open "Browse Templates->Image->Qwen image"

-Workflow: comfy_wf_qwen_image.json

### Benchmark
GGUF Q4_K_M

Resolution: 1328x1328

Sampler: 25 Steps


- sage-attention: 219s
- Pytorch Attention: 245s


## Qwen Edit

Workflow: comfy_wf_qwen_edit_safetensorGGUF.json

Action  | link                                                                                                                              | save to
---     |---                                                                                                                                | ---
GETFILE |   |ComfyUI/user/default/workflows
GETFILE | https://huggingface.co/QuantStack/Qwen-Image-Edit-GGUF/resolve/main/Qwen_Image_Edit-Q6_K.gguf                                     |ComfyUI/models/unet
GETFILE | https://huggingface.co/lightx2v/Qwen-Image-Lightning/resolve/main/Qwen-Image-Lightning-8steps-V1.0.safetensors                    |ComfyUI/models/loras
GETFILE | https://huggingface.co/Comfy-Org/Qwen-Image_ComfyUI/resolve/main/split_files/text_encoders/qwen_2.5_vl_7b_fp8_scaled.safetensors  |ComfyUI/models/text_encoders
GETFILE | https://huggingface.co/Comfy-Org/Qwen-Image_ComfyUI/resolve/main/split_files/vae/qwen_image_vae.safetensors  	                    |ComfyUI/models/vae  
CLONEIT | https://github.com/city96/ComfyUI-GGUF                                                                                            |ComfyUI/custom_nodes 
 

### Benchmark

1024x1024, 8steps. Q6_K

- sage-attention:   84s. 7.2s/it
- Pytorch Attention: 109s. 11.4s/it



## WAN2.2 AIO (uncensored)

You can 

Workflow: comfy_wf_wan2.2-ti2v-aio.json

### Benchmark
640x640, 4Steps, length: 81


**Text2Video Generation** (less time is better):
- sage-attention: 145s 24s/it
- Pytorch Attention: 191s 36s/it

**Image2Video Generation** (less time is better)

- sage-attention: 175s 32s/it
- Pytorch Attention: 220s  45s/it