LTX2.3-ICEdit-Insight
	
	
LTX2.3-ICEdit-Insight is a task-aware video restoration and editing model family developed by JoyFox Lab, built on top of the LTX-2.3 DiT-based audio-video foundation model.

This release focuses on four practical video editing directions:

Video Restoration: degradation recovery, compression cleanup, blur and noise reduction, and damaged detail restoration.
Video HD Enhancement: super-resolution, detail reconstruction, texture sharpening, and perceptual quality improvement.
Watermark Removal: logo cleanup, semi-transparent overlay removal, and occlusion-aware background reconstruction.
Subtitle Removal: hard subtitle removal, caption cleanup, text overlay removal, and temporally stable inpainting.
Unlike conventional frame-level enhancement pipelines, this model family operates as a generative video restoration system in latent video space. It is designed to preserve global structure, camera motion, object identity, and temporal consistency while reconstructing missing or degraded visual content.

Project links: GitHub project | JoyFox on Hugging Face

📦 Model Files
File	Purpose
ltx-2.3-edit-insight-dev-fp8.safetensors	Unified Insight base checkpoint for LTX-2.3 editing
ltx2.3-video-restoration-general.safetensors	Video restoration, artifact cleanup, blur and noise recovery
ltx2.3-ic-video-upscale-general.safetensors	Video HD enhancement, super-resolution, and detail recovery
ltx2.3-ic-watermark-remove-general.safetensors	Watermark removal and occlusion-aware reconstruction
ltx2.3-ic-subtitles-remove-general.safetensors	Subtitle removal and text overlay cleanup
🎬 Showcase
Video Restoration	Video HD Enhancement
	
Watermark Removal	Subtitle Removal
	

Video Restoration	Video HD Enhancement
	
Watermark Removal	Subtitle Removal
	