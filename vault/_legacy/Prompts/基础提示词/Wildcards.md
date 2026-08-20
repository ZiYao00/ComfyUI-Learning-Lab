
---

[Umi-AI-Embeds](https://github.com/Klokinator/Umi-AI-Embeds) `sd-webui 的 Dynamic Wildcards 扩展插件的替代款`

##### 随机提示词-Wildcards-通配符占位符 [comfyui-dynamicprompts](https://github.com/adieyal/comfyui-dynamicprompts) 

[【教程】DynamicPrompt动态提示词_通配符&占位符](https://www.bilibili.com/video/BV1Nz421z7T8/?spm_id_from=333.999.0.0&vd_source=d29e797daededf679f62ea666c78d484) 


Random Prompts：随机输出
Combinatiorial Prompts：顺序输出

![[Pasted image 20240730132550.png]]
 
 [$ 表示占位，固定输出]


--------

[进阶法，随机输出文本]

将文件放到以下路径
`ComfyUI\custom_nodes\comfyui-dynamicprompts\wildcards`
并英文命名，如：abc.txt
在节点中输入  [    __abc__   ]

![[Pasted image 20240730134704.png]]

