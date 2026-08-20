JoyCapion Alpha2/Joy2
[在线演示demo](https://huggingface.co/spaces/fancyfeast/joy-caption-alpha-two) | [huggingface模型](https://huggingface.co/fancyfeast/llama-joycaption-alpha-two-hf-llava/tree/main) 
[Comfyui插件](https://github.com/chflame163/ComfyUI_LayerStyle?tab=readme-ov-file#update) | [Joy2安装篇](https://articles.zsxq.com/id_fxirrddz86qh.html) | [Joy2XY测试](https://articles.zsxq.com/id_8hb2tphtlwo0.html) 


---
 
下载模型
[Orenguteng/Llama-3.1-8B-Lexi-Uncensored-V2_百度](https://pan.baidu.com/s/1dOjbUEacUOhzFitAQ3uIeQ?pwd=4ypv) 
[unsloth/Meta-Llama-3.1-8B-Instruct_百度](https://pan.baidu.com/s/1mH1SuW45Dy6Wga7aws5siQ?pwd=w6h5) 
`存放到以下路径 ..ComfyUI/models/LLM `

下载模型 [siglip-so400m-patch14-384_百度](https://pan.baidu.com/s/1pkVymOsDcXqL7IdQJ6lMVw?pwd=v8wp)
`存放到以下路径 ..ComfyUI/models/clip `

下载模型 [cgrkzexw-599808_百度](https://pan.baidu.com/s/12TDwZAeI68hWT6MgRrrK7Q?pwd=d7dh) 
`存放到以下路径 ..ComfyUI/models/Joy_caption `

|         | ==Meta-Llama-3.1-8B-Instruct== | ==Llama-3.1-8B-Lexi-Uncensored-V2== |
| :-----: | ------------------------------ | ----------------------------------- |
|  设计理念   | 专注于理解和执行自然语言指令                 | 提供无需对齐或道德化过滤的响应                     |
| 训练数据和方法 | 包含指令和命令的语料，侧重指令响应              | 广泛的语言任务，包括书籍、文章、对话等                 |
|  上下文理解  | 特别优化以响应指令                      | 较好的上下文理解能力，不特别优化以响应指令               |
|  应用场景   | 聊天机器人、虚拟助手或自动化任务执行系统           | 内容生成、语言翻译等需要广泛语言理解的场景               |
|  性能和效率  | 在执行特定任务时更高效和准确                 | 处理复杂语言任务时表现出色，但不一定在所有任务上都有最优效率      |
|  微调和定制  | 微调侧重于提升对特定类型指令的响应能力            | 针对特定应用场景进行微调，以提高特定任务上的表现            |

---

[Caption type：反推类型]
![[Pasted image 20241012162451.png]]
	`Descriptive #描述性` 
	`Descriptive (Informal) #描述性(非正式)` 
	`Training Prompt #训练提示` 
	`MidJourney #mj提示词` 
	`Booru tag list #类似Booru的标签列表` 
	`Booru-like tag list #类似Booru的标签列表` 
	`Art Critic #艺术评论` 
	`Product Listing #产品列表` 
	`Social Media Post #社交媒体帖子` 

推荐：[Training Prompt] 和 [MidJourney]模式


[Joy2 Extra Options：额外选项]

![[Pasted image 20241012163454.png]]

---

如果图像中有人物/角色，你必须将其称为{name}
不要包含关于人物/角色不可改变的信息(如种族、 性别等)，但仍然要包含可改变的属性(如发型)
包含有关光照的信息
包含有关相机角度的信息
包含是否有水印的信息
包含是否有JPEG伪影的信息
如果是照片，请包含相关的相机信息(光圈、快门速度、ISO)
不要包含任何色情内容;保持PG级
不要提及图像的分辨率
你必须包含关于图像主观审美质量的信息，从低到非常高
包含有关图像构图风格的信息，例引导线、三分法则或对称性
不要提及图像中的任何文字
指定景深以及背景是聚焦还是模糊
如果适用，请提及可能使用的人工或自然光源
不要使用任何模棱两可的语言
包括图像是否是sfw.暗示性或nsfw
只描述图像中最重要的元素
指定描述中使用的角色名称tvcC

---

[refer_character_name 是否在生成的描述中引用角色名称]
`开启后，描述中会提到指定的角色名称，例如 "Huluwa"。`
[exclude_people_info 是否排除与人物相关的信息]
`开启后，会忽略人物的外貌、年龄、性别等信息，不涉及任何与人物相关的内容。
[include_lighting 是否在描述中包含光照信息]
`开启后，描述会涉及到光线的来源、光线强度、光线方向等相关信息。`
[include_camera_angle 是否在描述中包含相机的角度信息]
`开启后，描述会包含相机的拍摄角度，如高角度、低角度、俯视、仰视等。`
[include_watermark 是否在描述中包含水印信息]
`开启后，会在描述中提到图片中是否有水印。`
[include_JPEG_artifacts 是否包含 JPEG 压缩失真（如压缩噪点、伪影）的描述]
`开启后，描述会指出图像中的 JPEG 压缩伪影或其他相关的压缩问题。`
[include_exif 是否包含图像的 EXIF 数据信息（如拍摄设备、设置）]
`开启后，描述会包括关于相机设备、拍摄设置（如 ISO、光圈、快门速度等）的信息。`
[exclude_sexual 是否排除与性别或性相关的描述]
`开启后，任何与性别或性相关的描述将被排除。`
[exclude_image_resolution 是否排除图像分辨率的描述]
`开启后，描述中不会提到图像的分辨率或清晰度信息。`
[include_aesthetic_quality 是否包含对图像美学质量的评价]
`开启后，描述中会评估图像的美学质量，如色彩平衡、构图、细节处理等。`
[include_composition_style 是否包含对图像构图风格的描述]
`开启后，描述会提到图像的构图方式，如对称性、黄金分割、视线引导等。`
[exclude_text 是否排除文本内容的描述]
`开启后，描述中不会包含图像中的任何文本或标注内容。`
[specify_depth_field 是否在描述中包含景深信息]
`开启后，描述会包含景深效果的描述，如前景清晰、背景模糊等。`
[specify_lighting_sources 是否详细描述光源]
`开启后，描述会包括光源的类型、数量和位置等详细信息。`
[do_not_use_ambiguous_language 是否避免使用模糊语言]
`开启后，描述中不会使用模糊或不确定的语言，描述会更加明确和具体。`
[include_nsfw 是否包含不适合公开观看的（NSFW）内容的描述]
`开启后，生成的描述会包括与不适合公开观看的内容相关的元素。`
[only_describe_most_important_elements 是否仅描述最重要的元素]
`开启后，描述中只会包含图像中最核心、最重要的部分，不涉及次要或细节部分。
[character_name（填入值为 “Huluwa”）指定描述中使用的角色名称]
`当前设置："Huluwa"，表示描述将引用这个名称。`


