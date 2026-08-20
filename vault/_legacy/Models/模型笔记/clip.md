
### **旧：text_encoders → 新：clip**

##### flux文本编码器

clip_g.safetensors 
clip_l.safetensors 

可替换上面2个
ViT-L-14-TEXT-detail-improved-hiT-GmP-HF.safetensors
ViT-L-14-TEXT-detail-improved-hiT-GmP-TE-only-HF.safetensors

	“TEXT”模型具有出色的提示跟随性，尤其是对于文本，也对于其他细节。
	“SMOOTH” 模型有时**可以有更好的细节（当图像中没有文字时）
	“GmP” 初始微调已弃用/不如上述模型。


【Long_clip】Flux的文本编码器的长文本微调模型CLIP-L
longclip-L.pt #基础
Long-ViT-L-14-GmP-ft.safetensors	 #升级
Long-ViT-L-14-BEST-GmP-smooth-ft.safetensors #升级



#####  Flux-PuLID 模型
EVA02_CLIP_L_336_psz14_s6B



【hunyuan & FramePack】文本模型
llava_llama3_fp8_scaled.safetensors

----------------------------------

【JoyCaption2】https://github.com/StartHua/Comfyui_CXH_joy_caption
siglip-so400m-patch14-384

----------------------------------
【Wan万相视频】文本模型
umt5_xxl_fp8_e4m3fn_scaled
umt5_xxl_fp16
umt5_xxl_KJ_enc_fp8_e4m3fn

【Wan万相视频】 clip模型
open-clip-xlm-roberta-large-vit-huge-14_visual_fp16.safetensors
open-clip-xlm-roberta-large-vit-huge-14_visual_fp32.safetensors

----------------------------------

【FramePack】
clip_l
llava_llama3_fp8_scaled
llava_llama3_fp16