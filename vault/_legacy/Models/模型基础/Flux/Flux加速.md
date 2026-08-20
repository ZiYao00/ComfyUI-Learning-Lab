
Flux加速方法，包括模式、节点、插件、编译环境

|         画质         | 参数                                      | 加速  |          要求           |             缺点             | GGUF | Lora |
| :----------------: | --------------------------------------- | --- | :-------------------: | :------------------------: | :--: | ---- |
|   SageAttention    | Patch Sage Attention KJ节点<br>选择Auto     | 10% |  安装环境SageAttentionx   |                            |  ✔   | ✔    |
|      步数Steps       | 20步/25步/28步                             |     |                       |                            |      |      |
|        fast        | fp8_e4m3fn_fast                         | 40% |        40系以上显卡        |       改变see<br>画质略降        |  ✔   | ✔    |
|   torch compile    |                                         | 35% | 安装环境triton<br>30系以上显卡 | 改变see<br>画质略降<br>换分辨率要重新编译 |  ❌   | ✔    |
|     Tea Cache      | 0.2—加速效果差<br>0.25—改变构图                  | 10% |         安装插件          |           画质略有下降           |  ✔   | ✔    |
| First Block Cachex | 0.07—丢失细节<br>0.12—适合抽卡                  | 40% |     安装插件WaveSpeed     |           画质略有下降           |  ✔   | ✔    |
|       加速Lora       | 阿里Turbo<br>guidacne 3.8<br>步数：8<br>权重：1 |     |                       |                            |  ✔   | ✔    |
|                    | 混元Hyper<br>步数：8<br>权重：0.125             |     |                       |                            |  ✔   | ✔    |
|  Schnell<br>（模型）   | 步数：4-6                                  |     |                       |                            |  ✔   | ✔    |

节点串联方式
【model】
【lora】
【TeaCache，Tea加速】
【Apply First Block Cache，FB加速】
【Patch Model Patcher Order，lora补丁】
【TorchCompileModel，图像编译】
【Patch Sage Attention KJ，SageAttention】