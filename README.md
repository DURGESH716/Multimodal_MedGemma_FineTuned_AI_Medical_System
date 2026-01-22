#  MedGemma LoRA – Medical Image Captioning (Gradio App)

This project fine-tunes MedGemma 1.5–4B (Image + Text) using LoRA for
medical image captioning and deploys it with Gradio.

> Model weights are not stored in this repository.
> They are downloaded automatically at runtime from Hugging Face.

---

## Requirements

### System
- Linux (Ubuntu recommended)
- Python ≥ 3.10
- NVIDIA GPU (16GB+ VRAM recommended)
- CUDA 12.x
---


## Step 1: Create Virtual Environment

```bash
python3 -m venv .venv311
source .venv311/bin/activate
````

---

## Step 2: Install Dependencies

```bash
pip install --upgrade pip
pip install -r requirements.txt
```

---

## Step 3: Base Model Download

The base model is downloaded automatically when first used.

Model:

```
google/medgemma-1.5-4b-it
```

Expected directory after first run:

```
models/medgemma-1.5-4b-it
```

No manual download is required.

---

## Step 4: Train LoRA Adapter

Run this only if you want to fine-tune on your own dataset.

```bash
CUDA_VISIBLE_DEVICES=0 python train_.py
```

Output:

```
medgemma-lora-output/
├── adapter_config.json
└── adapter_model.safetensors
```

---

## Step 5: Test LoRA Adapter

Verify inference using the trained adapter.

```bash
CUDA_VISIBLE_DEVICES=0 python test_lora.py
```

Example output:

```
Predicted Caption:
Based on the medical image, the lungs appear...
```

---

## Step 6: Launch Gradio App

Start the web interface:

```bash
CUDA_VISIBLE_DEVICES=0 python gradio_app.py
```

You will see:

```
Running on local URL:  http://0.0.0.0:7860
Running on public URL: https://xxxx.gradio.live
```

