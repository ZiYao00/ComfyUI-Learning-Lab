
```
对于[CMD]
cd /d G:\AIGC\ComfyUI\.ext

对于[PowerShell]
cd G:\AIGC\ComfyUI\.ext

输入 activate 激活虚拟环境
```

```
python.exe -m pip install  #安装依赖命令

```


### 以下举例如何安装 [ apex ] 库

```
cd /d G:\AIGC\ComfyUI\.ext

python.exe -m pip uninstall apex

git clone https://www.github.com/nvidia/apex

cd apex

python.exe -m pip setup.py install --cuda_ext --cpp_ext

```

python.exe -m pip setup.py install --cuda_ext --cpp_ext 


---

输入以下命令进行安装

```
#假如文件在Scripts根目录下
pip install natten-0.17.2.dev0-py311-none-win_amd64.whl

pip install triton-3.1.0-cp311-cp311-win_amd64.whl

python.exe -m pip install G:\AIGC\Lib.app\natten-0.17.2.dev0-py311-none-win_amd64.whl

#假如文件在其它任意路径
` pip install T:\Users\Downloads\natten-0.17.2.dev0-py311-none-win_amd64.whl
```


```

G:\AIGC\ComfyUI\.ext\python.exe -m pip install #使用指定的python虚拟环境安装 

G:\AIGC\ComfyUI\.ext\python.exe -m from apex import amp

```