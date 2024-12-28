# F5-TTS

F5-TTS is a cutting-edge text-to-speech (TTS) framework designed for high-quality, customizable, and efficient voice generation. Built with advanced deep learning technologies, F5-TTS supports multi-lingual and multi-speaker capabilities, enabling natural and expressive speech synthesis.

---

## Features

- **Multi-Speaker and Multi-Lingual Support:** Generate voices in different languages and tones.
- **Custom Voice Fine-Tuning:** Train or fine-tune models with your own dataset.
- **Flexible Deployment:** Supports both inference and training setups.
- **Gradio Integration:** Easy-to-use web interface for TTS inference and fine-tuning.
- **Docker Support:** Simplifies deployment with pre-built Docker images.

---

## Installation

### Prerequisites
- Python 3.10
- CUDA 11.6+ (for GPU support)
- FFmpeg (required for audio processing)

### 1. Environment Setup
```bash
conda create -n f5-tts python=3.10
conda activate f5-tts
```

### 2. Install PyTorch
Install a PyTorch version compatible with your CUDA version:
```bash
pip install torch==1.13.1+cu116 torchaudio==0.13.1+cu116 --extra-index-url https://download.pytorch.org/whl/cu116
```

### 3. Install F5-TTS
Choose one of the following methods:

#### A. As a Pip Package
For inference only:
```bash
pip install git+https://github.com/SWivid/F5-TTS.git
```

#### B. Editable Installation
For training and fine-tuning:
```bash
git clone https://github.com/SWivid/F5-TTS.git
cd F5-TTS
git submodule update --init --recursive
pip install -e .
```

#### C. Docker Installation
Build the Docker image:
```bash
docker build -t f5tts:v1 .
```
Or pull the pre-built image:
```bash
docker pull ghcr.io/swivid/f5-tts:main
```

---

## Usage

### 1. Inference
#### Gradio Web Interface
Launch the Gradio app for TTS inference:
```bash
f5-tts_infer-gradio
```
Options:
- **Custom Port:** `f5-tts_infer-gradio --port 7860`
- **Host:** `f5-tts_infer-gradio --host 0.0.0.0`
- **Shareable Link:** `f5-tts_infer-gradio --share`

#### Command-Line Interface (CLI)
Run inference from the command line:
```bash
f5-tts_infer-cli --model "F5-TTS" \
    --ref_audio "ref_audio.wav" \
    --ref_text "The content, subtitle or transcription of reference audio." \
    --gen_text "Some text you want TTS model generate for you."
```

### 2. Training and Fine-Tuning
Launch the Gradio interface for training:
```bash
f5-tts_finetune-gradio
```
Refer to the training documentation for detailed instructions.

---

## Requirements

- **Libraries:**
  - PyTorch
  - Torchaudio
  - FFmpeg
  - FastAPI
  - Gradio

- **System:**
  - CUDA-enabled GPU for optimal performance
  - Python 3.10 environment

---

## Troubleshooting

### Common Issues

1. **FFmpeg Not Found**
   Ensure FFmpeg is installed and added to your system PATH.

2. **Too Much Data for Declared Content-Length**
   Increase the server buffer size or use chunked data streaming.

### Verifying Installation
Test the setup with:
```bash
python -c "import torch; print(torch.cuda.is_available())"
```

---

---


