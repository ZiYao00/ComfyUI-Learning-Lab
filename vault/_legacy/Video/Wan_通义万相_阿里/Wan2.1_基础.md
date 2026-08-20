
[通义万相Wan2.1入门_黎黎源上咩](https://www.bilibili.com/video/BV1WkXGY7EuT/?spm_id_from=333.1007.tianma.2-2-5.click&vd_source=d29e797daededf679f62ea666c78d484) 
[官方comfy和kijai万相视频评测对比_啦啦啦小黄瓜](https://www.bilibili.com/video/BV1TERNYBEW7/?spm_id_from=333.1387.upload.video_card.click&vd_source=d29e797daededf679f62ea666c78d484)  

|                 |            Comfy             |            Kijai             |
| --------------- | :--------------------------: | :--------------------------: |
| clip            |              ❌               |       `..\models\clip`       |
| clip_vision     |   `..\models\clip_vision`    |              ❌               |
| diffusers_model | `..\models\diffusion_models` | `..\models\diffusion_models` |
| text_encode     |  `..\models\text_encoders`   |  `..\models\text_encoders`   |
| vae             |       `..\models\vae`        |       `..\models\vae`        |

### ComfyUI官方WanVideo模型下载地址

**clip_vison模型下载**：**[点击下载](https://huggingface.co/Comfy-Org/Wan_2.1_ComfyUI_repackaged/resolve/main/split_files/clip_vision/clip_vision_h.safetensors?download=true)** 
该模型需要放置在`ComfyUI/models/clip_vision`

**text_encoders模型下载：[点击下载](https://huggingface.co/Comfy-Org/Wan_2.1_ComfyUI_repackaged/resolve/main/split_files/text_encoders/umt5_xxl_fp8_e4m3fn_scaled.safetensors?download=true) 
该模型放置在`ComfyUI/models/text_encoders`

**vae模型下载：[点击下载](https://huggingface.co/Comfy-Org/Wan_2.1_ComfyUI_repackaged/resolve/main/split_files/vae/wan_2.1_vae.safetensors?download=true)** 
该模型放置在`ComfyUI/models/vae`

**diffusion_model模型下载：[点击下载](https://huggingface.co/Comfy-Org/Wan_2.1_ComfyUI_repackaged/tree/main/split_files/diffusion_models)**。
该模型放置在`ComfyUI/models/diffusion_models`

### Kijai WanVideo模型下载

模型下载地址（模型全部汇聚在一个网页）：[点击跳转](https://huggingface.co/Kijai/WanVideo_comfy/tree/main)，
[注意] 这里的**clip_vison**模型放置在`ComfyUI/models/clip`文件夹而不是clip_vison中 

wan21，FP16>Q8>FP8>Q6