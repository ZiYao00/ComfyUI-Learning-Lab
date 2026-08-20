
| 模型       | Sampler | Scheduler    | Shift | CFG | 画面  | 步数  | 帧数    | 分辨率     |
| -------- | ------- | ------------ | ----- | --- | --- | --- | ----- | ------- |
| wan21    | uni_pc  | simple       | 8     | 6   | 柔和  |     | 16+插帧 | 480x832 |
| wan22    | euler推荐 | simple       | 8     | 3.5 | 柔和  | 3+3 | 16+插帧 | 480x832 |
|          | euler a | simple       | 8     | 3.5 | 柔和  | 3+3 | 16+插帧 | 480x832 |
|          | ipndm   | sgm_uniform  |       | 1   |     | 3+3 | 16+插帧 | 480x832 |
|          | res_2s  | bong_tangent | 1、4   | 1   |     | 3+3 | 16+插帧 | 480x832 |
| FusionX  | euler   | beta         | 1     | 1   | 锐利  |     |       | 480x832 |
| lightx2v |         |              |       |     | 锐利  |     |       | 480x832 |

 - #### 大模型选择
GGUF：      量化Q4，速度快，与fp16/fp8区别不大。
FP8/FP18：画面清晰，速度一般

|           | 风格   | 优势  | 提示词遵从 | 采样器           | 推荐lora          | Sage | 文生视频 |
| --------- | ---- | --- | ----- | ------------- | --------------- | ---- | ---- |
| DaSiWa    | 二次元  | 兼容  | 普通    | euler/euler a | SVI             |      | 无    |
| Remix     | 半真实  | 稳   | 强     | euler/euler a | 可有可无            | 开    | 人物欧美 |
| SmoothMix | 动态写实 | 动态强 | 普通    | euler/euler a | SVI<br>lightx2v | 开    | 画面靓丽 |

 - #### 采样算法 [ModelSamplingSD3]（算法位移）- **shift** 值
 数值：5（文生视频）
 数值：8（图生视频）


 - #### 最优解

|     | 采样器             | Lora高噪                          | Lora低噪                           | Sage加速 | shift | clip     |
| --- | --------------- | ------------------------------- | -------------------------------- | ------ | ----- | -------- |
| 图生  | euler / euler a | SVI，0.75<br>lightx2v_4step_1022 | SVI，0.75<br>lightx2v_t2v_rank128 | 开      | 8     | 可有<br>可无 |
| 首尾  | euler / euler a | SVI，0.75                        | SVI，0.75                         | 开      | 8     | 可有<br>可无 |
| 文生  | euler / euler a |                                 |                                  |        | 5     | 可有<br>可无 |


 - #### 声音 MMAudio

| 模型                                          | 优点   | 缺点      |
| ------------------------------------------- | ---- | ------- |
| mmaudio_large_44k_nsfw_gold_8.5k_final_fp16 | 速度快  | 声音偏NSFW |
| mmaudio_large_44k_v2                        | 速度更快 |         |



---
#### [教程：SmoothMix+Remix+Dasiwa◆wan2.2全套精简工作流](https://www.bilibili.com/video/BV188Ngz3Ejd/?spm_id_from=333.1007.tianma.1-1-1.click&vd_source=d29e797daededf679f62ea666c78d484)  
[下载：模型+插件+工作流](https://pan.quark.cn/s/55e9257870c1)   

---

- #### Lora选择

 ~~**传统（放弃）**~~

```


高噪
	wan21_lightx2v_KJ \ lightx2v_i2v_14B_480_cfg_step_distill_rank128_bf16，强度3

低噪
	wan21_lightx2v_KJ \ lightx2v_i2v_14B_480_cfg_step_distill_rank128_bf16，强度1

```


 **新玩法（推荐），最优搭配**

[加速lora：lightx2v] + [SVI长视频lora]
优点：加速
缺点：

```

高噪
	wan22_Lightning_KJ \ wan22_i2v_A14B_High_noise_lora_rank64_lightx2v_4step_1022，强度1
	 ### 版本说明：1217，画面崩坏；推荐1022版本。）
	 ### 强度1：画面稳定
	 ### 强度1.2：画面稳定，速度稍微加快
	 ### 强度2.5：画面稳定，速度快，整体画面偏冷
	
	SVI \ SVI_v2_PRO_Wan2.2-I2V-A14B_HIGH_lora_rank_128_fp16，强度1

低噪
	wan21_lightx2v_KJ \ lightx2v_t2v_14B_cfg_step_distill_v2_lora_rank128_bf16，强度1.5
	
	SVI \ SVI_v2_PRO_Wan2.2-I2V-A14B_LOW_lora_rank_128_fp16，强度1
	

```

[首尾帧]
高低噪均使用 [1022]lora，强度：1。


 **其它Lora，可加可不加**
 
[奖励lora：Unified_Reward_Flex；增强物理]
优点：增强画面稳定性，即动画连贯
缺点：慢动作

```

高噪
	Rewards \ wan22_t2v_UnifiedReward_Flex_LoRA_HIGH_rank64_bf16增强物理
	

低噪
	Rewards \ wan22_t2v_UnifiedReward_Flex_LoRA_LOW_rank64_bf16增强物理


```


[奖励lora：VBVR]
优点：增强画面稳定性，即动画连贯
缺点：慢动作

```
高噪
	Rewards \ wan22_i2v_VBVR_HIGH_rank_64_fp16慢动作动画连贯，强度1 ~ 1.5，推荐1.5
```


---

#####  [插件：PainterI2V]

**优点**：增强动态
**缺点**：会抑制画面，变成慢动作


*motion_amplitude 参数值说明*

| 运动类型        | 推荐参数      | 示例提示词     |
| ----------- | --------- | --------- |
| 快速（跑步 / 跳跃） | 1.25–1.35 | 快速向前奔跑    |
| 正常（走路 / 挥手） | 1.10–1.20 | 流畅地行走     |
| 动态增强        | 1.00–1.10 | 略微增强动态和运镜 |

**[结论：不推荐]**

---

#### **Tips 技巧** 


- #### 如何保持动作幅度和面部一致性比较均衡

[大模型-高躁] 
wan22-EnhancedNSFW_FastMove_fp8_High_V2 *（Fast Move V2版是动作快速版）* 

[大模型-低噪] 
wan22-DaSiWa-i2v_MidnightFlirt_Low_V7 *（V7更强的一致性，V8、V8.1和V9都不是很好）* 



- #### 长视频lora：SVI
在超过5S的视频，可增强长视频的稳定性。配置高可达到15S。

[Wan2.2-SVI-I2V-A14B_High](https://huggingface.co/Kijai/WanVideo_comfy/blob/main/LoRAs/Stable-Video-Infinity/v2.0/SVI_v2_PRO_Wan2.2-I2V-A14B_HIGH_lora_rank_128_fp16.safetensors) ，推荐强度：0.75 或 1
[Wan2.2-SVI-I2V-A14B_Low](https://huggingface.co/Kijai/WanVideo_comfy/blob/main/LoRAs/Stable-Video-Infinity/v2.0/SVI_v2_PRO_Wan2.2-I2V-A14B_LOW_lora_rank_128_fp16.safetensors)  ，推荐强度：0.75 或 1



 - #### 加速技术：SageAttention

强度：1/4
影响：会有慢动作效果


