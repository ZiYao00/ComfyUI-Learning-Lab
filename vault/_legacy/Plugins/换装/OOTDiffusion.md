插件 https://github.com/AuroBit/ComfyUI-OOTDiffusion?tab=readme-ov-file

视频教程 https://www.bilibili.com/video/BV1Ew4m1d7Bn/?spm_id_from=333.337.search-card.all.click&vd_source=d29e797daededf679f62ea666c78d484

------------------------------------
`启动`
`C:\Users\YAO\.conda\envs\ootd\python.exe main.py`

`python路径`
`C:\Users\YAO\.conda\envs\ootd`

`创建虚拟环境`
`conda create -n ootd python=3.10`

`激活此【ootd】环境路径，并开始部署`
conda activate ootd

conda install pytorch torchvision torchaudio pytorch-cuda=12.1 -c pytorch -c nvidia

conda install cuda-nvcc -c nvidia

`在conda虚拟环境中，CD到节点目录下，安装依赖`
pip install -r custom_nodes/ComfyUI-OOTDiffusion/requirements.txt

conda install cuda-nvcc -c nvidia


**注意：不要从 Installer 点击启动 terminal**

进入 `C:\Program Files (x86)\Microsoft Visual Studio\2022\BuildTools\VC\Auxiliary\Build` 目录， 
右击进入 terminal，注意要用CMD 不要 powershell。

启动 native x64 target x64 的编译环境变量（兼容环境下 nvcc 编译会报错）：
vcvars64.bat
