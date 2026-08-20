

[GitHub - kijai/ComfyUI-HunyuanVideoWrapper](https://github.com/kijai/ComfyUI-HunyuanVideoWrapper) 

文件：
[原版bf16] hunyuan video t2v_720p_bf16.safetensors 
[官网KiJia_fp8]hunyuan video 720 cfgdistill fp8_e4m3fn.safetensors
[city96_GGUF]...gguf
[FastVideo]hunyuan video FastVideo t2v-720p.pt

----
### 提示词

[要求]
简短的两到三句英文，token<250

[镜头切换咒语]
The camera then switches to,镜头切换到

----

### 参数

| 分辨率  |   9:16   |   16:9   |   4:3    |   3:4    |   1:1   |
| :--: | :------: | :------: | :------: | :------: | :-----: |
| 540p | 544*960  | 960*544  | 624*832  | 832*624  | 720*720 |
| 720p | 720*1280 | 1280*720 | 1104*832 | 832*1104 | 960*960 |

|  帧数  |  9  | 85  | 125 |     257     |
| :--: | :-: | :-: | :-: | :---------: |
| 4N+1 |     |     |     | 超过200帧内容会重复 |

| 采样器 |                    |        |
| :-: | :----------------: | :----: |
|  ✨  |       Euler        | Simple |
|  ✨  |      Dpmpp 2M      |  Beta  |
| 👑  | Dpmpp 2s ancestral |  Beta  |

length：帧数 `1帧为文生图，测试9`
steps：步数 `20~50，推荐30` 
ModelSamplingSD3_shift：当步数≧30，shift推荐7，当步数≦20，shift推荐9或以上
