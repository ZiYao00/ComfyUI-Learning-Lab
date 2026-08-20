Florence2具有检测对象、对象分割、图片识别、图片反推、图片询问、文字识别、生成提示词等多种功能的模型

[【B站视频教程】图像视觉技术Florence 2详细使用教学](https://www.bilibili.com/video/BV1MSYQeTELm/?spm_id_from=333.337.search-card.all.click&vd_source=d29e797daededf679f62ea666c78d484) 

---

~~[florence_dw基础版](https]//github.com/yiwangsimple/florence_dw)···`不推荐`

[ComfyUI-Florence2/kijai版](https]//github.com/kijai/ComfyUI-Florence2)  `模型存放路径 ComfyUI/models/LLM`
[【星球】语义分割、图像文本（英文！）识别、图像反推于一体插件：ComfyUI-Florence2](https://articles.zsxq.com/id_7k920ftepmjc.html)

---

[葫芦娃版] 
[蒙版Florence2Ultra](https://github.com/chflame163/ComfyUI_LayerStyle?tab=readme-ov-file#Florence2Ultra) 笔记[[Florence2 Ultra]]
[提示词反推Florence2Image2Prompt](https://github.com/chflame163/ComfyUI_LayerStyle?tab=readme-ov-file#Florence2Image2Prompt)  笔记[[Florence2Image2Prompt2]]

[【星球】关于layerstyle插件LayerUtility: Florence2 反推、抠图讲解（葫芦娃）](https://articles.zsxq.com/id_0mjvc7fdg86d.html)

---

| 模型说明                       |             |     |
| -------------------------- | ----------- | --- |
| base                       | 基础          |     |
| base-ft                    | 基础-微调       |     |
| large                      | 大型          |     |
| large-ft                   | 大型-微调       |     |
| DocVQA                     | 文档视觉问答      |     |
| SD3-Captioner              | SD3         |     |
| base-PromptGen             | 基础提示生成器     |     |
| CogFlorence-2-Large-Freeze |             |     |
| CogFlorence-2.1-Large      |             |     |
| base PromptGen-v1.5        | 基础提示生成器v1.5 |     |
| large-PromptGen-v1.5       | 大型提示生成器v1.5 |     |
`存放路径 ComfyUI/models/florence2`

[base]`基础版本的模型，提供基本功能和性能
[base-ft]`基础版本的模型，并经过进一步微调 (fine-tuning) 以提升某些特定任务的性能
[large]`大规模模型，通常包含更多参数和更强的性能，适用于更复杂的任务
[large-ft]`大规模模型并经过进一步微调，结合大模型的强大能力和特定任务的优化
[DocVQA]`专为文档问答 (Document Visual Question Answering) 任务设计和优化的模型，可处理图片型文档
[SD3-Captioner]`专门用于图像描述 (captioning) 的模型，可能是针对第三版的标准（如SD3）进行优化
[base-PromptGen]`基础版本的提示生成 (Prompt Generation) 模型，可能用于生成文本提示或输入

**[经测试反推使用bass、或者SD3挺好]**

---

![[Florence2_task.png]]
##### 模式选择

[region  caption] `检测基础对象（带编号，带遮罩），描述对象内容`
[dense region caption] `检测更多的对象（带编号，带遮罩），描述检测到的对象内容
[region proposal] `检测所有的对象（带编号，带遮罩），但不描述`
[caption]  `简要描述，自然语言`
[detailed caption] `详细的描述，自然语言`
[more detailed caption] `超详细的描述，自然语言`
[caption to phrase grounding] `根据提示词分割对象，输出bbox蒙版`
[referring expression segmentation] `根据提示词分割对象，输出对象蒙版`
[OCR] `OCR文字提取，仅支持英文`
[OCR with region] `检测区域并OCR文字提取`
[DocVQA] `识别图片上的文档，进行问答或总结`
[prompt gen tags] `生成标签式提示词`
[prompt gen mixed caption] `自然语言与标签文本混合`