# 🎨 Simple Text-to-Image Generator (Stable Diffusion)

This project is a **Text-to-Image AI Generator** built with  
[Hugging Face Diffusers](https://huggingface.co/docs/diffusers/index) and [Gradio](https://www.gradio.app/).

It allows you to type any text prompt and instantly generate a beautiful image using the **Stable Diffusion v1.5** model.

---

## 🧠 Overview

Stable Diffusion is a deep learning model that converts **text descriptions into images**.  
It works by starting with random noise and iteratively refining it based on your prompt using a process called **diffusion**.

This app provides an easy-to-use **web UI** to interact with the model — no complex setup needed.

---

## 🚀 Features

✅ Simple and clean Gradio interface  
✅ Adjustable **Steps** (quality/speed tradeoff)  
✅ Adjustable **Guidance Scale** (prompt adherence)  
✅ Choose output image size (Small, Medium, Default)  
✅ GPU/CPU compatible (runs fastest on Google Colab GPU)  
✅ Shareable public link via `gradio.live`

---

## 🧩 Tech Stack

| Component | Description |
|------------|-------------|
| **Model** | [Stable Diffusion v1.5](https://huggingface.co/runwayml/stable-diffusion-v1-5) |
| **Framework** | [Diffusers by Hugging Face](https://github.com/huggingface/diffusers) |
| **Backend** | [PyTorch](https://pytorch.org/) |
| **UI** | [Gradio](https://gradio.app/) |
| **Runtime** | Google Colab / Local Python |

---

## 🖼️ Screenshots

### 🧠 Gradio Interface
![Colab Output](https://github.com/nagasivaninandam/Text-to-Image-Generator/blob/master/Gradio%20app.png)

### 🦊 Example Output 1 – “A watercolor fox in the forest”
![Gradio App](https://github.com/nagasivaninandam/Text-to-Image-Generator/blob/master/Gradio%20app.png)

### 🌅 Example Output 2 – “A cozy reading nook by a window”
![Generated Image 2](output.png)

---

## ⚙️ How It Works

### 1. Load the model
The **Stable Diffusion Pipeline** includes:
- CLIP text encoder (understands your prompt)
- U-Net (removes noise)
- VAE (decodes latent space to image)

### 2. Generate
Each run:
1. Takes your text prompt  
2. Starts from pure noise  
3. Denoises step-by-step (`num_inference_steps`)  
4. Uses **guidance scale** to control how strictly it follows your text  
5. Outputs a high-quality image

---

## 🧪 Parameters

| Parameter | Description | Recommended |
|------------|-------------|--------------|
| **Steps** | Number of denoising iterations. Higher = better quality, slower. | 15–25 |
| **Guidance** | How closely to follow the prompt. Too high = distorted. | 6–8 |
| **Size** | Output resolution. | Small (384) for CPU, 512 for GPU |

---

## ⚡ Quick Start

### 🖥️ Local Run
```bash
# Clone and enter project
git clone https://github.com/<yourusername>/text-to-image-generator.git
cd text-to-image-generator

# Create environment
python -m venv venv
venv\Scripts\activate   # (Windows)
# or source venv/bin/activate (Linux/Mac)

# Install dependencies
pip install torch diffusers transformers accelerate safetensors gradio

# Run the app
python app.py
