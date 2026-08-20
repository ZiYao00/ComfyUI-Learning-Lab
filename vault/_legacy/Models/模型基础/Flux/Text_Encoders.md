
##### **返回目录>>>[[FLUX详细说明]]** 

**[ Text Encoders文本编码器 ]**

文本优化插件1 [ComfyUI-Long-CLIP](https://github.com/SeaArtLab/ComfyUI-Long-CLIP) [[Long-CLIP]]

文本优化插件2 [ComfyUI-ResAdapter](https://github.com/jiaxiangc/ComfyUI-ResAdapter) [[ResAdapter]]


```
文件说明

├── [clip文本]，标签式
│   ├── clip_l.safetensors 
│   ├── clip_g.safetensors 
│   └── # other
│   
├── clip-l的微调，可替换上面2个
│   ├──ViT-L-14-TEXT-detail-improved-hiT-GmP-HF.safetensors
│   ├──ViT-L-14-TEXT-detail-improved-hiT-GmP-TE-only-HF.safetensors
│   ├──# other
│      
├── [t5文本]，自然语言
│   ├──t5xxl_fp8_e4m3fn.safetensors
│   ├──t5xxl_fp16.safetensors
│   ├──
│   
├── [Long-CLIP]，增强文本token，
│   ├──longclip-L.pt
│   ├──Long-ViT-L-14-GmP-ft.safetensors
│   └──Long-ViT-L-14-BEST-GmP-smooth-ft.safetensors
│   
└── ...
``` 

