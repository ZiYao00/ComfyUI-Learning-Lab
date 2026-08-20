
[eddy路亚的lora收藏夹](https://huggingface.co/eddy1111111/lightx2v_it2v_adaptive_fusionv_1.safetensors/tree/main) 

| 文件名                                                | 社区实测/口碑                                                | 一句话总结                               |
| -------------------------------------------------- | ------------------------------------------------------ | ----------------------------------- |
| FullDynamic_Ultimate_Fusion_Elite<br><br>运动幅度【暴力】  | 测试画面“抖到糊”，怀疑是放大运动 latent 的 LoRA。                       | 纯民间魔改，暴力加大运动幅度，极易崩帧，官方没认领。          |
| lightx2v_it2v_adaptive_fusion<br><br>运动幅度【保守】      | 和Elite 版比，运动幅度更小，融合权重随噪声下降而减弱，崩帧率略低。                   | 可以理解为“ Elite 的保守版”，一样是非官方私炉。        |
| WAN22_MoCap_fullbodyCOPY_ED<br><br>强制全身            | 其实是把“半身”动作 LoRA 强行改 key 成“全身”，精度很差，作者自己都备注了 COPY，不建议用。 | 半身转全身的半成品试验品，无实用价值。                 |
| Wan2.2-Fun-A14B-InP-Fusion-Elite<br><br>融合官方奖励lora | 把官方 Reward-LoRA + 自己额外训的 3000 张“高动态”素材混合重炼的私炉。         | 非官方，能用但不可商用，效果类似“官方 Reward + 运动增强”。 |
| lightx2v_elite_it2v_animate_face<br><br>表情增强       | 实测会把人脸 latent 单独拎出来做二次驱动，表情幅度大，容易出现口型崩坏。               | 人脸表情增强 LoRA，娱乐向，别上正式片。              |
| wan2.2_face_complete_distilled<br><br>人脸解码加速       | 实测推理速度 +15 %，人脸细节略糊，远景看不出差别。                           | 人脸解码蒸馏加速包，非 LoRA，可换可不换。             |
