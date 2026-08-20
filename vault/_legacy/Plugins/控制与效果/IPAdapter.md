
#### [风格迁移ComfyUI\IPAdapter_plus](https://github.com/cubiq/ComfyUI_IPAdapter_plus) 

##### [模型说明] 
`ipadapter存放路径可自定义修改，只需要修改的extra_model_paths.yaml里的存放位置即可`
##### 1、[clip_vision] `路径存放：..\ComfyUI\models\clip_vision` 

| CLIP-ViT-H-14-laion2B-s32B-b79K.safetensors    |            |
| ---------------------------------------------- | ---------- |
| CLIP-ViT-bigG-14-laion2B-39B-b160k.safetensors |            |
| clip-vit-large-patch14-336.bin                 | 仅适用于Kolors |

---
##### 2、[ipadapter] `路径存放：..\ComfyUI\models\ipadapter` 

|                                             |                                       |
| ------------------------------------------- | ------------------------------------- |
| ip-adapter_sd15.safetensors                 | 基础模型，平均强度                             |
| ip-adapter_sd15_light_v11.bin               | 光影响模型                                 |
| ip-adapter-plus_sd15.safetensors            | Plus型号，非常强大                           |
| ip-adapter-plus-face_sd15.safetensors       | 脸部模型，肖像                               |
| ip-adapter-full-face_sd15.safetensors       | 更强的人脸模型，但并不一定更好                       |
| ip-adapter_sd15_vit-G.safetensors           | 基础模型，需要 bigG clip vision 编码器          |
| ip-adapter_sdxl_vit-h.safetensors           | SDXL 模型                               |
| ip-adapter-plus_sdxl_vit-h.safetensors      | SDXL plus 型号                          |
| ip-adapter-plus-face_sdxl_vit-h.safetensors | SDXL 人脸模型                             |
| ip-adapter_sdxl.safetensors                 | vit-G SDXL 模型，需要 bigG clip vision 编码器 |
| ❌ip-adapter_sd15_light.safetensors          | [弃用]❌v1.0 光影响模型                       |

---
##### 3、[ipadapter-faceid] `路径存放：..\ComfyUI\models\ipadapter` 

|                                            |                    |
| ------------------------------------------ | ------------------ |
| ip-adapter-faceid_sd15.bin                 | 基础 FaceID 模型       |
| ip-adapter-faceid-plusv2_sd15.bin          | FaceID plus v2     |
| ip-adapter-faceid-portrait-v11_sd15.bin    | 人像文字提示风格转换         |
| ip-adapter-faceid_sdxl.bin                 | SDXL 基础 FaceID     |
| ip-adapter-faceid-plusv2_sdxl.bin          | SDXL plus v2       |
| ip-adapter-faceid-portrait_sdxl.bin        | SDXL文本提示风格转换       |
| ip-adapter-faceid-portrait_sdxl_unnorm.bin | 非常强的风格仅传输 SDXL     |
| ❌ip-adapter-faceid-plus_sd15.bin           | [弃用]FaceID plus v1 |
| ❌ip-adapter-faceid-portrait_sd15.bin       | [弃用]肖像模型 v1        |

---
##### 4、[ipadapter-lora] `路径存放：..\ComfyUI\models\loras` 

|                                                |                                  |
| ---------------------------------------------- | -------------------------------- |
| ip-adapter-faceid_sd15_lora.safetensors        |                                  |
| ip-adapter-faceid-plusv2_sd15_lora.safetensors |                                  |
| ip-adapter-faceid_sdxl_lora.safetensors        | SDXL FaceID LoRA                 |
| ip-adapter-faceid-plusv2_sdxl_lora.safetensors | SDXL plus v2 LoRA                |
| ❌ip-adapter-faceid-plus_sd15_lora.safetensors  | [弃用]用于已弃用的FaceID plus v1模型的 LoRA |
|                                                |                                  |

---
##### 5、社区模型[ipadapter-lora] `路径存放：..\ComfyUI\models\loras` 

|                                      |                                                                      |
| ------------------------------------ | -------------------------------------------------------------------- |
| ip_plus_composition_sd15.safetensors | [忽略风格和内容的通用组合](https://huggingface.co/ostris/ip-composition-adapter) |
| ip_plus_composition_sdxl.safetensors | SDXL 版本                                                              |
| Kolors-IP-Adapter-Plus.bin           | IPAdapter Plus 适用于 Kolors 型号                                         |
| Kolors-IP-Adapter-FaceID-Plus.bin    | Kolors 模型的 IPAdapter FaceIDv2。                                       |
`注意：Kolors 在 InsightFace antelopev2模型上进行训练 ，您需要手动下载并将其放在models/inisghtface目录中。` [antelopev2模型](https://huggingface.co/MonsterMMORPG/tools/tree/main) 




