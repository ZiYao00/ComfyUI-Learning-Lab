[ 收缩模型Unet： PatchModelAddDownscale (Kohya Deep Shrink)  ] 
突破模型的分辨率限制

![[Pasted image 20241113170848.png]] 

[block_number 层编号]：决定收缩哪个层，参数：1-6，默认：3

[downscale_factor 缩放系数]：针对unet里的层缩放

[start_percent开始时间] 和 [end_percent结束时间]，控制unet收缩介入的时间