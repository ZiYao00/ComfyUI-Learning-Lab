
![[Pasted image 20240910153650.png]]
[ControlNet说明_优设](https://www.uisdc.com/controlnet-3)

[ControlNet官方下载地址](https://huggingface.co/lllyasviel/sd_control_collection/tree/main)

|               |     |                                       |
| ------------- | --- | ------------------------------------- |
| ip2p          |     | 图像迭代性很强,可以用于生成很多细节变化的图像               |
| shuffle       |     | 图像混洗,可以随机调换图像的像素位置,造成扭曲变形的效果          |
| depth         |     | 深度感知,可以估计图像的深度信息并生成 depth map         |
| Canny         |     | 边缘检测,用于检测图像中的边缘                       |
| inpaint       |     | 图像修复,可以用来填补图像中的损坏或遗失的区域               |
| lineart       |     | 生成线条艺术风格的图像                           |
| mlsd          |     | 直线检测                                  |
| normalbae     |     | 从单张图像中估计表面法线和 profundity，用于3D重建       |
| openpose      |     | 人体姿态估计,可以检测图像或视频中的人体以及人体姿态            |
| scribble      |     | 利用简单的涂鸦生成图像,涂鸦提供局部纹理和结构信息,算法会换算出完整的图像 |
| seg           |     | 图像分割,可以分割出图像中的不同类别区域                  |
| softedge      |     | 产生软化的边缘效果,使边缘变得模糊不清                   |
| lineart_anime |     | 生成 anime 风格的线条艺术图像                    |
| Tile          |     | 分块放大，利用平铺技术扩展图像边界,生成重复平铺的效果           |
|               |     |                                       |
| Union         |     |                                       |
