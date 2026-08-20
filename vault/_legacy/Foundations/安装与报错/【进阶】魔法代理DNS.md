
[在ComfyUI中使用hf-mirror解决访问HuggingFace的网络问题](https://www.bilibili.com/opus/952567877332893714) 

[设置 comfyui 、github 走代理]

```

REM 配置Git代理
git config --global http.proxy http://127.0.0.1:7890
git config --global https.proxy http://127.0.0.1:7890

REM 设置HTTP和HTTPS代理
set HTTP_PROXY=http://127.0.0.1:7890
set HTTPS_PROXY=http://127.0.0.1:7890

REM 刷新DNS
ipconfig /flushdns

# 取消方法
git config --global --unset http.proxy
git config --global --unset https.proxy

```
`最后的7890是端口号，每台电脑都不同，【开始菜单】-【设置】-【网络】-【代理】，就能看到了`

[刷新DNS]
```
# Windows
ipconfig /flushdns

# Linux
systemctl restart nscd或者 /etc/init.d/nscd restart

# Mac
sudo killall -HUP mDNSResponder
```

[临时禁用代理]
```
# Windows 命令提示符 
set HTTPS_PROXY= 
set HTTP_PROXY= 

PowerShell 
$env:HTTPS_PROXY="" 
$env:HTTP_PROXY=""
```

[取消 Git 的全局代理]
```
# 取消
git config --global --unset http.proxy
git config --global --unset https.proxy

# 检查（没任何输出即正常）
git config --global --get http.proxy  
git config --global --get https.proxy  

```

[网络加速]
```
# 查询网址的IP
nslookup github.com

# 在hosts文件添加 C:\Windows\System32\drivers\etc
20.205.243.166 github.com
```
