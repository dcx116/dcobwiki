---
id: 84f4f165-de59-4b24-b3a9-b1837863ae37
title: Hugging Face
source: https://huggingface.co/joyfox/LTX2.3-ICEdit-Insight
author:
published:
created: 2026-05-11
description: We’re on a journey to advance and democratize artificial intelligence through open source and open science.
tags:
  - clippings
模型类型: model
daimodeltype: lora
daibasemodel: LTX2.3
模型应用: 视频
模型作用: 去除字幕
封面: +dcshare/daiassets/附件/595f4276320acc346f554e87bfe6bbd1_MD5.webp
下载地址: https://huggingface.co/joyfox/LTX2.3-ICEdit-Insight/tree/main
cssclasses:
file:
---
## LTX2.3-ICEdit-Insight

| ![[+dcshare/daiassets/附件/595f4276320acc346f554e87bfe6bbd1_MD5.webp]] | ![[+dcshare/daiassets/附件/b6ac81b544a6dd6a646d6253645cc58f_MD5.webp]] |
| -------------------------------------------------------------------- | -------------------------------------------------------------------- |
| ![[+dcshare/daiassets/附件/b7b7bc666eea228b09975e3a24ae888c_MD5.webp]] | ![[+dcshare/daiassets/附件/ff18e0cba3ef0ba1900a0cee2dc0a031_MD5.webp]] |

**LTX2.3-ICEdit-Insight** is a task-aware video restoration and editing model family developed by **JoyFox Lab**, built on top of the **LTX-2.3 DiT-based audio-video foundation model**.

This release focuses on four practical video editing directions:

- **Video Restoration**: degradation recovery, compression cleanup, blur and noise reduction, and damaged detail restoration.
- **Video HD Enhancement**: super-resolution, detail reconstruction, texture sharpening, and perceptual quality improvement.
- **Watermark Removal**: logo cleanup, semi-transparent overlay removal, and occlusion-aware background reconstruction.
- **Subtitle Removal**: hard subtitle removal, caption cleanup, text overlay removal, and temporally stable inpainting.

Unlike conventional frame-level enhancement pipelines, this model family operates as a **generative video restoration system** in latent video space. It is designed to preserve global structure, camera motion, object identity, and temporal consistency while reconstructing missing or degraded visual content.

Project links: [GitHub project](https://github.com/Valiant-Cat/LTX2-ICEdit-Insight) | [JoyFox on Hugging Face](https://huggingface.co/joyfox)

## 📦 Model Files

| File                                             | Purpose                                                      |
| ------------------------------------------------ | ------------------------------------------------------------ |
| `ltx-2.3-edit-insight-dev-fp8.safetensors`       | Unified Insight base checkpoint for LTX-2.3 editing          |
| `ltx2.3-video-restoration-general.safetensors`   | Video restoration, artifact cleanup, blur and noise recovery |
| `ltx2.3-ic-video-upscale-general.safetensors`    | Video HD enhancement, super-resolution, and detail recovery  |
| `ltx2.3-ic-watermark-remove-general.safetensors` | Watermark removal and occlusion-aware reconstruction         |
| `ltx2.3-ic-subtitles-remove-general.safetensors` | Subtitle removal and text overlay cleanup                    |

## 🎬 Showcase

| **Video Restoration**                                                                                                                                                              | **Video HD Enhancement**                                                                                                                                                                       |
| ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| ![[+dcshare/daiassets/附件/595f4276320acc346f554e87bfe6bbd1_MD5.webp]]                                                      | ![[+dcshare/daiassets/附件/b6ac81b544a6dd6a646d6253645cc58f_MD5.webp]] |
| **Watermark Removal**                                                                                                                                                              | **Subtitle Removal**                                                                                                                                                                           |
| ![[+dcshare/daiassets/附件/b7b7bc666eea228b09975e3a24ae888c_MD5.webp]] | ![[+dcshare/daiassets/附件/ff18e0cba3ef0ba1900a0cee2dc0a031_MD5.webp]]              |

| **Video Restoration**                                                                                                                                                                          | **Video HD Enhancement**                                                                                                                                                                          |
| ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| ![[+dcshare/daiassets/附件/87f16e1bd57c6432695c1253a60bbe61_MD5.webp]] | ![[+dcshare/daiassets/附件/8440711c3204e17ec26801201448f899_MD5.webp]] |
| **Watermark Removal**                                                                                                                                                                          | **Subtitle Removal**                                                                                                                                                                              |
| ![[+dcshare/daiassets/附件/524a13ec865409ec754b8ac8d01b1a31_MD5.webp]]          | ![[+dcshare/daiassets/附件/9ad4dc3d374abdee5e6d1cad3e282439_MD5.webp]]              |

## 🚀 Script Usage

Run all scripts from the project root.

```bash
bash run_restoration.sh
bash run_hd.sh
bash run_hd.sh /path/to/input.mp4
bash run_watermark_rm.sh
bash run_watermark_rm.sh /path/to/input.mp4
bash run_subtitle_rm.sh
bash run_subtitle_rm.sh /path/to/input.mp4
```

## 💻 Command Examples

### Video Restoration

```bash
PYTORCH_CUDA_ALLOC_CONF=expandable_segments:True \
python run_pipeline.py \
  --mode restoration \
  --video ./inputs/input_480p.mp4 \
  --prompt "Convert the video to ultra-high-definition quality while removing artifacts and rebuilding high-frequency details." \
  --output ./outputs/output_restoration.mp4 \
  --height 1184 --width 704 --num-frames 97 \
  --fps 24.0 --seed 42 \
  --sigma-profile workflow \
  --streaming-prefetch-count 2 \
  --model-checkpoint ./models/checkpoints/ltx-2.3-edit-insight-dev-fp8.safetensors \
  --lora ./models/loras/ltx2.3-train/ltx2.3-video-restoration-general.safetensors
```

### Video HD Enhancement

```bash
PYTORCH_CUDA_ALLOC_CONF=expandable_segments:True \
python run_pipeline.py \
  --mode hd \
  --video ./inputs/input_480p.mp4 \
  --prompt "Convert the video to ultra-high-definition quality, significantly improving clarity, fine detail richness, texture fidelity, and overall perceptual sharpness." \
  --output ./outputs/output_hd.mp4 \
  --height 1184 --width 704 --num-frames 97 \
  --fps 24.0 --seed 42 \
  --sigma-profile workflow \
  --streaming-prefetch-count 2 \
  --model-checkpoint ./models/checkpoints/ltx-2.3-edit-insight-dev-fp8.safetensors \
  --lora ./models/loras/ltx2.3-train/ltx2.3-ic-video-upscale-general.safetensors
```

### Watermark Removal

```bash
PYTORCH_CUDA_ALLOC_CONF=expandable_segments:True \
python run_pipeline.py \
  --mode watermark_rm \
  --video ./inputs/input_480p.mp4 \
  --prompt "Remove short-video platform watermarks and related occlusions from the video, restoring a clean, clear, and natural original image." \
  --output ./outputs/output_watermark_rm.mp4 \
  --height 1184 --width 704 --num-frames 97 \
  --fps 24.0 --seed 1546 \
  --sigma-profile workflow \
  --streaming-prefetch-count 2 \
  --model-checkpoint ./models/checkpoints/ltx-2.3-edit-insight-dev-fp8.safetensors \
  --lora ./models/loras/ltx2.3-train/ltx2.3-ic-watermark-remove-general.safetensors
```

### Subtitle Removal

```bash
PYTORCH_CUDA_ALLOC_CONF=expandable_segments:True \
python run_pipeline.py \
  --mode subtitle_rm \
  --video ./inputs/input_480p.mp4 \
  --prompt "Remove subtitles, captions, and related text occlusions from the video, restoring a clean and natural underlying image." \
  --output ./outputs/output_subtitle_rm.mp4 \
  --height 1184 --width 704 --num-frames 97 \
  --fps 24.0 --seed 42 \
  --sigma-profile workflow \
  --streaming-prefetch-count 2 \
  --model-checkpoint ./models/checkpoints/ltx-2.3-edit-insight-dev-fp8.safetensors \
  --lora ./models/loras/ltx2.3-train/ltx2.3-ic-subtitles-remove-general.safetensors
```

## ✨ Key Improvements

### Task-Aware IC-Edit Framework

We introduce a task-aware IC-Edit training framework for LTX-2.3, where each restoration direction is optimized with dedicated instruction conditioning and task-specific IC-LoRA adapters.

The model is trained not only to improve visual quality, but also to understand the editing goal behind different restoration tasks, including watermark removal, subtitle cleanup, damaged region recovery, and high-definition enhancement.

### LTX-2.3 DiT Backbone Adaptation

The model family is built on the LTX-2.3 foundation architecture, a diffusion-transformer video model designed for high-fidelity image-to-video and video generation workflows.

Our adaptation targets video restoration by improving:

- latent-space editability
- instruction-following behavior
- frame-to-frame stability
- high-frequency detail recovery
- local reconstruction around degraded or occluded regions

### Spatiotemporal Consistency Optimization

Video restoration requires more than strong single-frame quality. We optimize temporal consistency so that restored areas remain stable across adjacent frames.

This reduces common artifacts such as:

- flickering textures
- unstable reconstructed backgrounds
- inconsistent watermark removal
- subtitle ghosting
- frame-wise color shift
- detail popping during motion

### Degradation-Aware Training Curriculum

The training curriculum covers realistic video defects including:

- compression artifacts
- motion blur
- sensor noise
- low-bitrate video
- text overlays
- hard subtitles
- semi-transparent watermarks
- platform logos
- local occlusions
- low-resolution inputs

This improves generalization across short videos, social-media clips, mobile footage, downloaded videos, and compressed production material.

### Occlusion-Aware Reconstruction

For watermark and subtitle removal, the model is optimized to reconstruct the hidden visual content behind occluded regions.

Instead of smearing or blurring the target area, it uses surrounding spatial context and temporal cues to infer plausible background structure, object boundaries, lighting, and texture continuity.

### Frequency-Enhanced HD Restoration

For HD enhancement, the model improves perceptual sharpness and fine visual detail through frequency-aware restoration training.

This is especially helpful for recovering:

- hair strands
- fabric texture
- skin detail
- product edges
- background patterns
- typography-like fine structures
- natural image clarity

## 🧠 Inference Notes

- Single-stage inference is recommended for most editing tasks.
- Two-stage refinement can improve visual polish but may weaken task-specific LoRA constraints.
- Watermark and subtitle removal perform best when the occlusion area is stable and not excessively large.
- HD enhancement quality depends on input resolution, motion complexity, and compression level.
- Higher output resolution improves detail but requires more VRAM.
- For strong-motion videos, conservative denoising settings are recommended to preserve temporal structure.
- Frame count should follow the `8k + 1` rule.
- Output height and width should be multiples of `32` in single-stage inference.

## 🏗️ Training

This model family was trained and optimized by **JoyFox Lab** (**Chengdu Xuanhu Technology Co., Ltd.**).

The training pipeline includes:

- task-aware video restoration data construction
- degradation synthesis and curriculum training
- IC-LoRA specialization for four editing directions
- temporal consistency regularization
- occlusion-aware reconstruction training
- high-frequency perceptual enhancement
- instruction-guided video editing optimization

## 📬 Contact

For research collaboration, commercial licensing, or workflow integration, contact:

- `z@vvicat.com`

## 📜 License

Licensed under **Apache 2.0**.

Please also review the license terms of the upstream LTX-2.3 base model when using or redistributing derivative checkpoints.

Inference Providers [NEW](https://huggingface.co/docs/inference-providers)

This model isn't deployed by any Inference Provider. [🙋 Ask for provider support](https://huggingface.co/spaces/huggingface/InferenceSupport/discussions/new?title=joyfox/LTX2.3-ICEdit-Insight&description=React%20to%20this%20comment%20with%20an%20emoji%20to%20vote%20for%20%5Bjoyfox%2FLTX2.3-ICEdit-Insight%5D\(%2Fjoyfox%2FLTX2.3-ICEdit-Insight\)%20to%20be%20supported%20by%20Inference%20Providers.%0A%0A\(optional\)%20Which%20providers%20are%20you%20interested%20in%3F%20\(Novita%2C%20Hyperbolic%2C%20Together%E2%80%A6\)%0A)

## Model tree for joyfox/LTX2.3-ICEdit-Insight

Base model

[Lightricks/LTX-2.3](https://huggingface.co/Lightricks/LTX-2.3)

Finetuned

([48](https://huggingface.co/models?other=base_model:finetune:Lightricks/LTX-2.3))

this model## LTX2.3-ICEdit-Insight

| ![[+dcshare/daiassets/附件/595f4276320acc346f554e87bfe6bbd1_MD5.webp]] | ![[+dcshare/daiassets/附件/b6ac81b544a6dd6a646d6253645cc58f_MD5.webp]] |
| -------------------------------------------------------------------- | -------------------------------------------------------------------- |
| ![[+dcshare/daiassets/附件/b7b7bc666eea228b09975e3a24ae888c_MD5.webp]] | ![[+dcshare/daiassets/附件/ff18e0cba3ef0ba1900a0cee2dc0a031_MD5.webp]] |

**LTX2.3-ICEdit-Insight** is a task-aware video restoration and editing model family developed by **JoyFox Lab**, built on top of the **LTX-2.3 DiT-based audio-video foundation model**.

This release focuses on four practical video editing directions:

- **Video Restoration**: degradation recovery, compression cleanup, blur and noise reduction, and damaged detail restoration.
- **Video HD Enhancement**: super-resolution, detail reconstruction, texture sharpening, and perceptual quality improvement.
- **Watermark Removal**: logo cleanup, semi-transparent overlay removal, and occlusion-aware background reconstruction.
- **Subtitle Removal**: hard subtitle removal, caption cleanup, text overlay removal, and temporally stable inpainting.

Unlike conventional frame-level enhancement pipelines, this model family operates as a **generative video restoration system** in latent video space. It is designed to preserve global structure, camera motion, object identity, and temporal consistency while reconstructing missing or degraded visual content.

Project links: [GitHub project](https://github.com/Valiant-Cat/LTX2-ICEdit-Insight) | [JoyFox on Hugging Face](https://huggingface.co/joyfox)

## 📦 Model Files

| File                                             | Purpose                                                      |
| ------------------------------------------------ | ------------------------------------------------------------ |
| `ltx-2.3-edit-insight-dev-fp8.safetensors`       | Unified Insight base checkpoint for LTX-2.3 editing          |
| `ltx2.3-video-restoration-general.safetensors`   | Video restoration, artifact cleanup, blur and noise recovery |
| `ltx2.3-ic-video-upscale-general.safetensors`    | Video HD enhancement, super-resolution, and detail recovery  |
| `ltx2.3-ic-watermark-remove-general.safetensors` | Watermark removal and occlusion-aware reconstruction         |
| `ltx2.3-ic-subtitles-remove-general.safetensors` | Subtitle removal and text overlay cleanup                    |

## 🎬 Showcase

| **Video Restoration**                                                                                                                                                              | **Video HD Enhancement**                                                                                                                                                                       |
| ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| ![[+dcshare/daiassets/附件/595f4276320acc346f554e87bfe6bbd1_MD5.webp]]                                                      | ![[+dcshare/daiassets/附件/b6ac81b544a6dd6a646d6253645cc58f_MD5.webp]] |
| **Watermark Removal**                                                                                                                                                              | **Subtitle Removal**                                                                                                                                                                           |
| ![[+dcshare/daiassets/附件/b7b7bc666eea228b09975e3a24ae888c_MD5.webp]] | ![[+dcshare/daiassets/附件/ff18e0cba3ef0ba1900a0cee2dc0a031_MD5.webp]]              |

| **Video Restoration**                                                                                                                                                                          | **Video HD Enhancement**                                                                                                                                                                          |
| ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| ![[+dcshare/daiassets/附件/87f16e1bd57c6432695c1253a60bbe61_MD5.webp]] | ![[+dcshare/daiassets/附件/8440711c3204e17ec26801201448f899_MD5.webp]] |
| **Watermark Removal**                                                                                                                                                                          | **Subtitle Removal**                                                                                                                                                                              |
| ![[+dcshare/daiassets/附件/524a13ec865409ec754b8ac8d01b1a31_MD5.webp]]          | ![[+dcshare/daiassets/附件/9ad4dc3d374abdee5e6d1cad3e282439_MD5.webp]]              |

## 🚀 Script Usage

Run all scripts from the project root.

```bash
bash run_restoration.sh
bash run_hd.sh
bash run_hd.sh /path/to/input.mp4
bash run_watermark_rm.sh
bash run_watermark_rm.sh /path/to/input.mp4
bash run_subtitle_rm.sh
bash run_subtitle_rm.sh /path/to/input.mp4
```

## 💻 Command Examples

### Video Restoration

```bash
PYTORCH_CUDA_ALLOC_CONF=expandable_segments:True \
python run_pipeline.py \
  --mode restoration \
  --video ./inputs/input_480p.mp4 \
  --prompt "Convert the video to ultra-high-definition quality while removing artifacts and rebuilding high-frequency details." \
  --output ./outputs/output_restoration.mp4 \
  --height 1184 --width 704 --num-frames 97 \
  --fps 24.0 --seed 42 \
  --sigma-profile workflow \
  --streaming-prefetch-count 2 \
  --model-checkpoint ./models/checkpoints/ltx-2.3-edit-insight-dev-fp8.safetensors \
  --lora ./models/loras/ltx2.3-train/ltx2.3-video-restoration-general.safetensors
```

### Video HD Enhancement

```bash
PYTORCH_CUDA_ALLOC_CONF=expandable_segments:True \
python run_pipeline.py \
  --mode hd \
  --video ./inputs/input_480p.mp4 \
  --prompt "Convert the video to ultra-high-definition quality, significantly improving clarity, fine detail richness, texture fidelity, and overall perceptual sharpness." \
  --output ./outputs/output_hd.mp4 \
  --height 1184 --width 704 --num-frames 97 \
  --fps 24.0 --seed 42 \
  --sigma-profile workflow \
  --streaming-prefetch-count 2 \
  --model-checkpoint ./models/checkpoints/ltx-2.3-edit-insight-dev-fp8.safetensors \
  --lora ./models/loras/ltx2.3-train/ltx2.3-ic-video-upscale-general.safetensors
```

### Watermark Removal

```bash
PYTORCH_CUDA_ALLOC_CONF=expandable_segments:True \
python run_pipeline.py \
  --mode watermark_rm \
  --video ./inputs/input_480p.mp4 \
  --prompt "Remove short-video platform watermarks and related occlusions from the video, restoring a clean, clear, and natural original image." \
  --output ./outputs/output_watermark_rm.mp4 \
  --height 1184 --width 704 --num-frames 97 \
  --fps 24.0 --seed 1546 \
  --sigma-profile workflow \
  --streaming-prefetch-count 2 \
  --model-checkpoint ./models/checkpoints/ltx-2.3-edit-insight-dev-fp8.safetensors \
  --lora ./models/loras/ltx2.3-train/ltx2.3-ic-watermark-remove-general.safetensors
```

### Subtitle Removal

```bash
PYTORCH_CUDA_ALLOC_CONF=expandable_segments:True \
python run_pipeline.py \
  --mode subtitle_rm \
  --video ./inputs/input_480p.mp4 \
  --prompt "Remove subtitles, captions, and related text occlusions from the video, restoring a clean and natural underlying image." \
  --output ./outputs/output_subtitle_rm.mp4 \
  --height 1184 --width 704 --num-frames 97 \
  --fps 24.0 --seed 42 \
  --sigma-profile workflow \
  --streaming-prefetch-count 2 \
  --model-checkpoint ./models/checkpoints/ltx-2.3-edit-insight-dev-fp8.safetensors \
  --lora ./models/loras/ltx2.3-train/ltx2.3-ic-subtitles-remove-general.safetensors
```

## ✨ Key Improvements

### Task-Aware IC-Edit Framework

We introduce a task-aware IC-Edit training framework for LTX-2.3, where each restoration direction is optimized with dedicated instruction conditioning and task-specific IC-LoRA adapters.

The model is trained not only to improve visual quality, but also to understand the editing goal behind different restoration tasks, including watermark removal, subtitle cleanup, damaged region recovery, and high-definition enhancement.

### LTX-2.3 DiT Backbone Adaptation

The model family is built on the LTX-2.3 foundation architecture, a diffusion-transformer video model designed for high-fidelity image-to-video and video generation workflows.

Our adaptation targets video restoration by improving:

- latent-space editability
- instruction-following behavior
- frame-to-frame stability
- high-frequency detail recovery
- local reconstruction around degraded or occluded regions

### Spatiotemporal Consistency Optimization

Video restoration requires more than strong single-frame quality. We optimize temporal consistency so that restored areas remain stable across adjacent frames.

This reduces common artifacts such as:

- flickering textures
- unstable reconstructed backgrounds
- inconsistent watermark removal
- subtitle ghosting
- frame-wise color shift
- detail popping during motion

### Degradation-Aware Training Curriculum

The training curriculum covers realistic video defects including:

- compression artifacts
- motion blur
- sensor noise
- low-bitrate video
- text overlays
- hard subtitles
- semi-transparent watermarks
- platform logos
- local occlusions
- low-resolution inputs

This improves generalization across short videos, social-media clips, mobile footage, downloaded videos, and compressed production material.

### Occlusion-Aware Reconstruction

For watermark and subtitle removal, the model is optimized to reconstruct the hidden visual content behind occluded regions.

Instead of smearing or blurring the target area, it uses surrounding spatial context and temporal cues to infer plausible background structure, object boundaries, lighting, and texture continuity.

### Frequency-Enhanced HD Restoration

For HD enhancement, the model improves perceptual sharpness and fine visual detail through frequency-aware restoration training.

This is especially helpful for recovering:

- hair strands
- fabric texture
- skin detail
- product edges
- background patterns
- typography-like fine structures
- natural image clarity

## 🧠 Inference Notes

- Single-stage inference is recommended for most editing tasks.
- Two-stage refinement can improve visual polish but may weaken task-specific LoRA constraints.
- Watermark and subtitle removal perform best when the occlusion area is stable and not excessively large.
- HD enhancement quality depends on input resolution, motion complexity, and compression level.
- Higher output resolution improves detail but requires more VRAM.
- For strong-motion videos, conservative denoising settings are recommended to preserve temporal structure.
- Frame count should follow the `8k + 1` rule.
- Output height and width should be multiples of `32` in single-stage inference.

## 🏗️ Training

This model family was trained and optimized by **JoyFox Lab** (**Chengdu Xuanhu Technology Co., Ltd.**).

The training pipeline includes:

- task-aware video restoration data construction
- degradation synthesis and curriculum training
- IC-LoRA specialization for four editing directions
- temporal consistency regularization
- occlusion-aware reconstruction training
- high-frequency perceptual enhancement
- instruction-guided video editing optimization

## 📬 Contact

For research collaboration, commercial licensing, or workflow integration, contact:

- `z@vvicat.com`

## 📜 License

Licensed under **Apache 2.0**.

Please also review the license terms of the upstream LTX-2.3 base model when using or redistributing derivative checkpoints.

Inference Providers [NEW](https://huggingface.co/docs/inference-providers)

This model isn't deployed by any Inference Provider. [🙋 Ask for provider support](https://huggingface.co/spaces/huggingface/InferenceSupport/discussions/new?title=joyfox/LTX2.3-ICEdit-Insight&description=React%20to%20this%20comment%20with%20an%20emoji%20to%20vote%20for%20%5Bjoyfox%2FLTX2.3-ICEdit-Insight%5D\(%2Fjoyfox%2FLTX2.3-ICEdit-Insight\)%20to%20be%20supported%20by%20Inference%20Providers.%0A%0A\(optional\)%20Which%20providers%20are%20you%20interested%20in%3F%20\(Novita%2C%20Hyperbolic%2C%20Together%E2%80%A6\)%0A)

## Model tree for joyfox/LTX2.3-ICEdit-Insight

Base model

[Lightricks/LTX-2.3](https://huggingface.co/Lightricks/LTX-2.3)

Finetuned

([48](https://huggingface.co/models?other=base_model:finetune:Lightricks/LTX-2.3))

this model