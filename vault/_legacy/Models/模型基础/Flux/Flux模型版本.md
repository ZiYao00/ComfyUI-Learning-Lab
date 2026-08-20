
##### **返回目录>>>[[FLUX详细说明]]** 

|         模型类型         | 开源  | 商业许可 | Local / Api |  性能  | 步数  |                                        |
| :------------------: | :-: | :--: | :---------: | :--: | :-: | :------------------------------------: |
|     Flux.1.1_Pro     |  ❌  |  ❌   |     API     | ⭐⭐🌟 | 20+ |                                        |
|      Flux.1_Pro      |  ❌  |  ❌   |     API     | ⭐⭐⭐  | 20+ |                                        |
|   Flux.1_dev_fp16    | ✔️  |  ❌   |    Local    |  ⭐⭐  | 20+ |                4090显卡起步                |
|    Flux.1_dev_fp8    | ✔️  |  ❌   |    Local    |  ⭐⭐  | 20+ |                                        |
| Flux.1_schnell_fp16  | ✔️  |  ✔️  |    Local    |  ⭐   | 1-4 |             约等于dev的turbo版本             |
|  Flux.1_schnell_fp8  | ✔️  |  ✔️  |    Local    |  ⭐   | 1-4 |             约等于dev的turbo版本             |
| GGUF<br>(Flux.1_dev) | ✔️  |  ✔️  |    Local    |  ⭐   | 20+ |   测试显卡：4070super<br>Q8_88秒 / Q4_45秒    |
|                      |     |      |             |      |     | 6G显存：Q4以下<br>8G显存：Q4-Q5<br>16G显存：Q5-Q6 |
|                      |     |      |             |      |     |                                        |
|        NF4-v2        | ✔️  |  ✔️  |    Local    |  ⭐   | 20+ |  4070super跑图，35秒<br>约等于Q4-Q5(gguf)水平   |
|                      |     |      |             |      |     |       整合clip、vae、T5文本<br>8G显卡就能跑       |
|                      |     |      |             |      |     |                                        |

---

黑森林版本： [黑森林版schnell模型](https://huggingface.co/black-forest-labs/FLUX.1-schnell/tree/main)  | [黑森林版dev模型](https://huggingface.co/black-forest-labs/FLUX.1-dev/tree/main) 

Comfy Org版本： [Comfy Org版dev模型](https://huggingface.co/Comfy-Org/flux1-dev/tree/main) | [Comfy Org版schnell模型](https://huggingface.co/Comfy-Org/flux1-schnell/tree/main) 

Kijia版本： [Kijia版dev模型及schnell模型](https://huggingface.co/Kijai/flux-fp8/tree/main) | 

[下载合集_夸克](https://pan.quark.cn/s/cf3dbed25c38) 

|    版本     |    类型    |       文件位置       |   数据格式   | 烘焙vae+clip | 生成步数  |
| :-------: | :------: | :--------------: | :------: | :--------: | :---: |
|    黑森林    |   dev    | diffusion_models |   bf16   |     ❌      |  20+  |
|           | schnell  | diffusion_models |   bf16   |     ❌      |  1-4  |
| Comfy Org |   dev    |   checkpoints    |   fp8    |     ✔️     |  20+  |
|           | schnell  |   checkpoints    |   fp8    |     ✔️     |  1-4  |
|   Kijia   |   dev    | diffusion_models |   fp8    |     ❌      |  20+  |
|           | schnell  | diffusion_models |   fp8    |     ❌      |  1-4  |
|   GGUF    |   dev    | diffusion_models |   fp8    |     ❌      |  20+  |
|  NF4-V2   |   dev    |   checkpoints    |   fp8    |     ✔️     |  20+  |
| Nunchaku  | int4/fp4 | diffusion_models | int4/fp4 |     ❌      | 4-12+ |
查看 [[模型兼容版本]]


