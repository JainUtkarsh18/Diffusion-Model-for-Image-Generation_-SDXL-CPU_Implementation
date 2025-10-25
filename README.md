# Diffusion Model for Image Generation-SDXL Pipeline Implementation on CPU.

This repository contains a **CPU-only implementation** of the Stable Diffusion XL (SDXL) pipeline using the Hugging Face **Diffusers** library.  
It is designed for environments without CUDA support, making it accessible on systems that only have CPU resources.

## Table of Contents      
        
- [Installation](#installation)       
- [Usage](#usage)
- [Example Prompt](#ExamplePrompt)
- [Features](#Features)
- [Output](#Output)
- [License](#license) 

--- 

## Installation

Run the following commands to set up the environment:

**Remove conflicting libraries**
```bash
pip uninstall -y xformers torch torchvision torchaudio peft || true
```

## Install PyTorch (CPU version)
```bash
pip install torch==2.4.0 torchvision==0.19.0 torchaudio==2.4.0
```

## Install required libraries
```bash
pip install diffusers==0.30.2 transformers==4.43.3 accelerate==0.33.0 \
safetensors==0.4.3 pillow==10.4.0 huggingface-hub==0.34.1
```

## Usage
Run the pipeline with:
```bash
python sdxl_pipeline.py
```
By default, the script will generate a cinematic motorcycle image using the SDXL Base model.

## Example Prompt
```vbnet
Prompt: "Cinematic shot of a cafe racer motorcycle on a rainy street at night, reflections, broken lights"
Negative Prompt: "motion blur, blown highlights, low quality, chromatic aberration, watermark"
```

## Features

Scheduler Options: Choose between ```dpmpp_2m```, ```euler_a```, or default schedulers.

Deterministic Seeds: Reproducible results via ```torch.manual_seed```.

Optimized for CPU: Enables VAE slicing & tiling for efficient memory usage.

Automatic Image Saving: Output images are saved in ```sdxl_out_cpu/```.

## Features

Generated images will be stored with filenames like:

```bash
sdxl_base_seed12345_g6.5_s28_w768_h768_YYYYMMDD_HHMMSS.png
```

## License

This project is for educational and research purposes.
Check the original Stability AI Stable Diffusion XL license before commercial use.



