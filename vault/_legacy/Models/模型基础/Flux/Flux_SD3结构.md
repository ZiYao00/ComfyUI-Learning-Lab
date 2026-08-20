
##### **返回目录>>>[[FLUX详细说明]]** 

[SD3 · Hugging Face](https://huggingface.co/lodestones/stable-diffusion-3-medium) 

各模型文件存放路径
	unet模型：`ComfyUI\models\unet`
	text_encoders文本编码器：`ComfyUI\models\clip`

```
SD3/Flux 文件结构
├── unet/
│   ├── flux1-dev-fp8.safetensors
│   ├── flux1-dev-Q6_K.gguf
│   └── # other Flux models
│
├── text_encoders/
│   ├── clip_g.safetensors
│   ├── clip_l.safetensors
│   ├── t5xxl_fp16.safetensors
│   └── t5xxl_fp8_e4m3fn.safetensors
│
└── ...
```
