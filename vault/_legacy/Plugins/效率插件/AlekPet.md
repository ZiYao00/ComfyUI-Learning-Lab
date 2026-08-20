
[ComfyUI_Custom_Nodes_AlekPet](https://github.com/AlekPet/ComfyUI_Custom_Nodes_AlekPet) 
翻译节点、预览文本、2D姿态图、绘画板- 手动画线条

---

[ 添加百度翻译api方法 ]

进入到插件目录内
`路径：..\ComfyUI\custom_nodes\ComfyUI_Custom_Nodes_AlekPet\DeepTranslatorNode` 

打开[config.json] 文件，手动加入 id与key，保存

```
"BaiduTranslator": {
        "appid": "这里", `这一行加入id`
        "appkey": 这里", `这一行加入key`
        "free_api": false,
        "show_service": true,
        "help": "appid and appkey"
```

