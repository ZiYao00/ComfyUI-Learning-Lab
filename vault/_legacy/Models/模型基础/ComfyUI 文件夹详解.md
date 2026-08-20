


```

📁ComfyUI_windows_portable
├── 📁ComfyUI                                          // comfy UI主要文件夹
│  ├── .git                                            // Git版本控制文件夹，代码版本管理用
│  ├── .github                                         // GitHub Actions 工作流文件夹
│  ├── 📁 comfy                                        // 
│  ├── 📁 comfy_extras                                 // 
│  ├── 📁 custom_nodes                                 // comfyUI 自定义节点文件目录（插件安装目录）
│  ├── 📁 input                                        // comfyUI上传文件夹，当你使用了如**load image**节点，对应上传的图片会存储到这个文件夹
│  ├── 📁 models                                       // 对应模型文件配置文件夹
│  |  ├── 📁 checkpoints                               // 检查点大模型文件存放路径
│  |  ├── 📁 clip                                      // CLIP文件存放路径
│  |  ├── 📁 clip_vision                               // CLIP_vision文件存放路径
│  |  ├── 📁 configs                                   
│  |  ├── 📁 controlnet                                // ControlNet 模型存放路径
│  |  ├── 📁 diffusers                                 
│  |  ├── 📁 embedding                                 // embedding 模型存放路径
│  |  ├── 📁 gligen                                
│  |  ├── 📁 hypernetworks                             // 超网络模型
│  |  ├── 📁 loras                                     // Lora 模型存放路径
│  |  ├── 📁 style_models                                
│  |  ├── 📁 unet                               
│  |  ├── 📁 upscale_models                            // upscale_models 放大模型存放路径
│  |  ├── 📁 vae                                       // VAE 模型存放路径
│  |  └── 📁 vae_approx                               
│  ├── 📁 notebooks
│  ├── 📁 user                                         // comfyUI 用户信息（如配置文件，工作流信息等）
│  |    ├── 📁 default                                 // 默认 comfyUI 用户文件夹
│  |    |    ├─ 📁 workflow                            // 用户保存的 workflow 文件
│  |    |    ├─ 📄 xxx.json                            // 用户的配置文件
│  |    |    └── ... xxx.json                          // 其它配置文件
│  |    └── ...[username]                              // 如果你启用了多用户且存在多用户则会显示对应不同用户的名称
│  ├── 📁 output                                       // comfyUI图片输出文件夹，当使用类似 ** save image** 节点时，生成的图片会存储到这个文件夹
│  |    ├── 📁 checkpoints                             // 如果有使用模型合并节点，和保存合并后的模型相关功能，则合并后的模型会输出到这里
│  |    └── ... xxx.png                                // 运行过程中生成的文件会保存到这里
│  ├── extra_model_paths.yaml.example                  //  额外模型文件路径配置文件，如设置此项，请删除**.example** 后缀用记事本进行编辑
│  └── ...                                             // 其它文件
├── config                                             // 配置文件夹
├── 📁 Python_embeded                                  // 嵌入的python 文件
├──📁 update                               
│  ├── update.py                                       // 用于comfyUI的 python 脚本
│  ├── update_comfyUI.bat                              // comfyUI作者推荐使用此批处理命令对 ComfyUI 进行升级
│  └── update_comfyui_and_python_dependencies.bat      // 只有当你的 python 依赖文件存在问题时才需要运行此批处理命令
├── comfyui.log                                        // Comfy UI运行日志文件
├── README_VERY_IMPORTANT.txt                          // README 文件，包含了文件使用的方法和说明等等
├── run_cpu.bat                                        // 批处理文件，当你的显卡为A卡或只有 CPU 时，双击运行它启动 ComfyUI
└── run_nvidia_gpu.bat                                 // 批处理文件，当你的显卡为N卡(Nvidia)时，双击运行它启动 ComfyUI

```