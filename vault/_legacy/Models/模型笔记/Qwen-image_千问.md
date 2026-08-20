

（model）-【ModelSamplingAuraFlow】shift: 3 -【CFGNorm】strength:1 -（model）

|       模型        |  采样器   |     调度器      | shift值 |
| :-------------: | :----: | :----------: | :----: |
|   Qwen-image    |        |              |        |
| Qwen-image-Edit | res_2s | bong_tangent |   3    |

### CFG值

| Model                    | Steps | CFG |
| ------------------------ | ----- | --- |
| Offical                  | 50    | 4.0 |
| fp8_e4m3fn               | 20    | 2.5 |
| fp8_e4m3fn + 4steps LoRA | 4     | 1.0 |

### Control值

- OpenPose 建议强度1.2-1.8(根据实际情况调整，比如原图半身，给的图是全身等)
- Depth：建议强度 0.75-1.5
- 结束时间可以调到0.2-0.8,当然1也可以，需要多测试，以免影响到原图
- openpose不想控制面部表情使用Openpose预处理器
- 出图崩了就适当降低强度值

| 名称    | 控制类型     | 强度       | 结束时间    |
| ----- | -------- | -------- | ------- |
| 动漫+人偶 | Depth    | 0.75-1.5 | 0.2-0.8 |
| 动漫+人偶 | OpenPose | 1.2-1.8  | 0.2-0.8 |
