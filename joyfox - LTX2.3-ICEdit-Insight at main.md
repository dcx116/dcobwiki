### Instructions to use joyfox/LTX2.3-ICEdit-Insight with libraries, inference providers, notebooks, and local apps. Follow these links to get started.

- Libraries
- [Diffusers](https://huggingface.co/joyfox/LTX2.3-ICEdit-Insight?library=diffusers)
    
    How to use joyfox/LTX2.3-ICEdit-Insight with Diffusers:
    
    pip install -U diffusers transformers accelerate
    
    import torch
    from diffusers import DiffusionPipeline
    
    # switch to "mps" for apple devices
    pipe = DiffusionPipeline.from_pretrained("joyfox/LTX2.3-ICEdit-Insight", dtype=torch.bfloat16, device_map="cuda")
    
    prompt = "Astronaut in a jungle, cold color palette, muted colors, detailed, 8k"
    image = pipe(prompt).images[0]
    
- Notebooks
- [Google Colab](https://huggingface.co/joyfox/LTX2.3-ICEdit-Insight/colab)
- [Kaggle](https://huggingface.co/joyfox/LTX2.3-ICEdit-Insight/kaggle)