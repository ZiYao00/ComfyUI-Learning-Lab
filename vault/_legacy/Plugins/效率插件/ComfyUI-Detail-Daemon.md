

[ComfyUI-Detail-Daemon](https://github.com/Jonseed/ComfyUI-Detail-Daemon) `ComfyUI-Detail-Daemon 添加细节插件`


![[Pasted image 20241101132807.png]]

[dishonesty_factor] `负值：减少sigmas，增加细节；正值：增加sigmas，减少细节；`

[增加细节] -0.08至-0.01是理想值，数值越小，细节越高，不会崩
[减少细节] 0.01-0.04为理想值，数值越大，细节越小，图像越模糊


![[Pasted image 20241101132946.png]]

start_percent开始调整时机

数值越低，细节越高，但会出现噪点；

单论相似度，起始值0.02起；

无噪点的话，0.09-0.1是最佳，建议默认0.1



---

[总结：通过以上测试，增加细节参数建议]

[dishonesty_factor] -0.08
[start_percent] 0.1
[end_percent] 0.9-1.0