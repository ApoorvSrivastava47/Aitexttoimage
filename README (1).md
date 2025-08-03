# 🖼️ Text-to-AI Image Generator

A **powerful and accessible AI-powered web application** that transforms your text prompts into stunning images using **Stable Diffusion v1.5**. Built with 🤗 Hugging Face’s `diffusers` and deployed via **Gradio** on Hugging Face Spaces, this project showcases the capabilities of modern generative AI in a clean, interactive interface.

---

## 🚨 What is This Project?

This notebook/web app allows users to:
- Enter **natural language prompts** like _“a futuristic city underwater”_.
- Instantly generate corresponding **high-resolution images** using Stable Diffusion.
- Interact via a **simple and fast web UI** built with Gradio.
- Run locally or deploy in the cloud (Hugging Face Spaces).

---

## ✨ Features

✅ **Text-to-Image Generation**  
Generate realistic, artistic, or surreal images directly from plain English text.

✅ **Stable Diffusion v1.5**  
Leverages a widely used, open-source deep learning model by Stability AI.

✅ **Modern Tech Stack**
- `diffusers` for inference pipelines
- `transformers` for tokenizer/backend support
- `Gradio` for user interface
- `safetensors` for optimized model weights

✅ **GPU Acceleration**  
Automatically utilizes CUDA for faster image generation (if available).

✅ **Easy to Deploy**  
Built to be deployed directly on Hugging Face Spaces with minimal setup.

---

## 📷 Demo

👉 **Live Hugging Face Space:**  
[https://<your-space-name>.huggingface.space](https://<your-space-name>.huggingface.space)  
_(Replace with your actual Hugging Face space URL)_

---

## 🧠 How It Works

1. The user enters a **text prompt** (e.g., `"a cat in a spacesuit on Mars"`).
2. The prompt is passed into the **Stable Diffusion pipeline**.
3. The model **generates a latent image**, which is decoded and returned.
4. The output image is **rendered via Gradio** in the browser.

---

## 🛠️ Setup Instructions

### 🔧 Dependencies
Install the necessary Python packages:

```bash
pip install diffusers==0.25.0 transformers accelerate gradio safetensors
```

You may also need to authenticate with the Hugging Face Hub to access model weights:

```python
from huggingface_hub import login
login("your-huggingface-token")  # paste your token here
```

### ▶️ Running Locally
```python
# Load the pipeline
pipe = StableDiffusionPipeline.from_pretrained("CompVis/stable-diffusion-v1-5", torch_dtype=torch.float16)
pipe.to("cuda")

# Define prompt
prompt = "a steampunk robot reading a book in a library"

# Generate image
image = pipe(prompt).images[0]
image.show()
```

### 🌐 Running with Gradio
```python
import gradio as gr

def generate(prompt):
    image = pipe(prompt).images[0]
    return image

gr.Interface(fn=generate, inputs="text", outputs="image").launch()
```

---

## 🧪 Example Prompts

- “a fantasy castle on a floating island”
- “a dog wearing VR glasses in a neon city”
- “an astronaut surfing on Saturn’s rings”
- “a Van Gogh-style painting of a city at night”

---

## 📁 Folder Structure

```
project/
│
├── app.ipynb               # Jupyter notebook with code
├── requirements.txt        # Package dependencies (optional)
├── README.md               # This file
```

---

## 📢 Credits

- Model: [Stable Diffusion v1.5](https://huggingface.co/runwayml/stable-diffusion-v1-5)
- Libraries: [🤗 diffusers](https://github.com/huggingface/diffusers), [Gradio](https://www.gradio.app/)
- Hosting: [Hugging Face Spaces](https://huggingface.co/spaces)

---

## 📜 License

This project is licensed under the [MIT License](LICENSE).  
Images generated may be subject to the Stable Diffusion license and community guidelines.
