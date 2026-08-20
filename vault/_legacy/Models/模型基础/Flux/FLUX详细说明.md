
#### [ 模型优势 ]

- 画质极佳，媲美MJ6
- 改进修手
- 字体生成与排版  `仅支持英文`
- 训练参数大，风格多样
- 分辨率弹性好      `512-1280区间都可以`
- embeddings通用性好     `SD1.5、SDXL通用`
- 不需要输入负面提示词

##### [[Flux模型版本]]
- Pro             `仅API调用`
- DEV FP16  `4090显卡起步`
- DEV FP8    `目前消费级版本`
- schnell FP16  `约等于DVE的turbo版本`
- schnell FP8
- GGUF   `4070super跑图，==Q8_88秒 / Q4_45秒`
⠀⠀⠀⠀⠀⠀⠀`6G显卡选Q4以下，8G选Q4-Q5`
⠀⠀⠀⠀⠀⠀⠀`16G显存推荐Q5-Q6模型`
- NF4     `4070super跑图，35秒，约等于Q4-Q5(gguf)水平`
⠀⠀⠀⠀⠀⠀⠀`整合clip、vae、T5文本，8G显卡就能跑`

-------

==**模型加载器说明**==

![[Pasted image 20240828145400.png]]
- unet加载器：加载`models\unet` 目录下的flux模型
- 传统加载器：加载`models\Stable-diffusion` 目录下的flux模型
- NF4加载器：加载`models\Stable-diffusion` 目录下的flux-NF4模型

![[Pasted image 20240828151822.png]]
- GGUF加载器：加载`models\unet` 目录下的flux模型

![[Pasted image 20240828145843.png]]
- default默认：加载fp16精度，即fp8_e5m2
- fp8_e4m3fn：fp8精度，节省一半资源


==**text_encoders 文本编码器说明**==  [[Text_Encoders]]

![[b4227081bda1727e01f3108dccc916d.png]]
![[Pasted image 20240828144754.png]]
- LongCLIPtextEncodeFlux：增强文本逻辑，将token长度从77扩展为248
- clip_l：标签式提示词，
- t5xxl：自然语言提示词，支持长文本
- `一般只输入t5文本即可，如果添加了lora，则需要填写clip_l文本。可复制为相同内容，也可clip_l填写标签式文本，t5填写自然语言文本。`
- Flux Guidance/引导：2-3.5
	1. 当值在1附近时，图像很可能会显得灰暗
	2. 当值在2附近时，更适合生成艺术绘画风格的图像
	3. 当值在3到3.5时，能应对不同场景
	4. 当值超过3.5时，图像的细节可能会增强，但对比度可能也会很高

---

[ ModelSamplingFlux ]

![[Pasted image 20241017165711.png]]
shift值
- 当数值较高时，模型会更加关注图像的结构
- 当数值较低时，模型会更加关注图像的细节

[如果放大图片，很明显较低的值会产生更平滑、细节更少的图像，但幻觉更少，较高的值会给你更多的细节，但也会有更多的噪音，所以你需要取得平衡。最大偏移的默认值为 1.15，基本偏移的默认值为 0.5，这些似乎是合理的值](https://www.reddit.com/r/comfyui/comments/1eugsf7/what_exactly_does_model_sampling_through_max/) 

---

==**采样器**==

- 采样器：euler
- 调度器：simple或beta
- 组合测试，以下5种最好
	1. ipdmn+simple
	2. uni_pc_bh2+simples
	3. euler+beta [推荐使用这个]
	4. euler+simple
	5. dpmpp+sgm_uniform
	6. uni_pc_bh2+sgm_uniform [网友推荐]
- CFG值：1，`高了图片会模糊
- 步数：DEV_20步以上，schnell_4-8步出图
- `FP8显存占用14-16G

|        | 采样           | 调度           |     |
| ------ | ------------ | ------------ | --- |
| 最高质量   | dpmpp_2m     | sgm_uniform  |     |
|        | dpmpp_sde    | karras       |     |
| 均衡     | euler        | sgm_uniform  |     |
|        |              | normal       |     |
| 创意与风格  | euler_a      | sgm_uniform  |     |
|        |              | karras       |     |
| 一致性与稳定 | ddim         | sgm_uniform  |     |
|        |              | ddim_uniform |     |
|        |              |              |     |
| 起手     | uni_pc       | beta         |     |
| 高质量    | dpm_2        | simple       |     |
| 电影级    | deis         | ddim_uniform |     |
|        |              |              |     |
| 未知     | dpmpp_2m     | simple       |     |
|        | ipdmn        | ddim_uniform |     |
| 其它     | dpm_adaptive | sgm_uniform  |     |
|        | ipdmn        | beta         |     |
|        |              |              |     |

| Nunchaku | 采样    | 调度           | 步数    |
| -------- | ----- | ------------ | ----- |
| 均衡-首选    | ipdmn | ddim_uniform | 20~30 |
| 速度       | euler | beta         |       |
|          | euler | simple       |       |
|          |       |              |       |
