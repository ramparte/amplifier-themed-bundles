# Local-First Setup Guide

This guide helps you configure Amplifier for fully offline, privacy-focused operation.

## Quick Start

1. Install a local LLM provider (Foundry Local or Ollama)
2. Download your preferred model
3. Configure Amplifier to use the local provider
4. Verify offline operation

---

## LLM Provider Setup

### Option A: Foundry Local (Recommended)

```bash
# Install Foundry Local
# Follow instructions at: https://github.com/microsoft/foundry-local

# Start the service
foundry-local start

# Verify it's running
foundry-local status
```

### Option B: Ollama

```bash
# Install Ollama
curl -fsSL https://ollama.ai/install.sh | sh

# Pull a model
ollama pull llama3.2
ollama pull codellama  # For coding tasks

# Start the server
ollama serve
```

---

## Model Selection Guide

### For General Use (Balanced)

| Model | Size | RAM Required | Best For |
|-------|------|--------------|----------|
| Phi-3-mini | 3.8B | 8GB | Fast responses, general chat |
| Llama 3.2 | 8B | 16GB | Quality responses, reasoning |
| Mistral | 7B | 16GB | Instruction following |

### For Coding Tasks

| Model | Size | RAM Required | Best For |
|-------|------|--------------|----------|
| CodeLlama | 7B | 16GB | Code completion, debugging |
| DeepSeek Coder | 6.7B | 16GB | Multi-language coding |
| Phi-3-medium | 14B | 32GB | Complex code reasoning |

### For Resource-Constrained Systems

| Model | Size | RAM Required | Notes |
|-------|------|--------------|-------|
| Phi-3-mini-4k | 3.8B | 6GB | Shorter context, faster |
| TinyLlama | 1.1B | 4GB | Very fast, basic tasks |
| Qwen2-0.5B | 0.5B | 2GB | Minimal footprint |

---

## Hardware Requirements

### Minimum Configuration
- CPU: 4 cores (AVX2 support recommended)
- RAM: 8GB
- Storage: 10GB free (for models)
- GPU: Not required (CPU inference works)

### Recommended Configuration
- CPU: 8+ cores (modern Intel/AMD)
- RAM: 16GB+
- Storage: SSD with 50GB+ free
- GPU: NVIDIA with 8GB+ VRAM (optional, accelerates inference)

### GPU Acceleration

For faster inference, configure GPU support:

```bash
# For NVIDIA GPUs (CUDA)
# Ensure CUDA toolkit is installed, then:
ollama run llama3.2 --gpu

# For AMD GPUs (ROCm)
# Requires ROCm-compatible Ollama build

# For Apple Silicon
# Metal acceleration is automatic
```

---

## Speech-to-Text Setup (whisper.cpp)

### Installation

```bash
# Clone and build whisper.cpp
git clone https://github.com/ggerganov/whisper.cpp
cd whisper.cpp
make

# Download a model (choose one)
./models/download-ggml-model.sh tiny.en    # Fast, English only
./models/download-ggml-model.sh base       # Balanced
./models/download-ggml-model.sh small      # Better accuracy
./models/download-ggml-model.sh medium     # High accuracy
```

### Model Comparison

| Model | Size | Speed | Accuracy |
|-------|------|-------|----------|
| tiny.en | 75MB | Very Fast | Good (English) |
| base | 142MB | Fast | Better |
| small | 466MB | Medium | Good |
| medium | 1.5GB | Slow | Very Good |
| large | 3GB | Very Slow | Excellent |

---

## Offline Workflow Tips

### 1. Pre-download Everything
Before going offline, ensure you have:
- LLM models downloaded
- Whisper models (if using STT)
- Any documentation you might need

### 2. Verify Offline Mode
```bash
# Disconnect from network and test
ping -c 1 8.8.8.8  # Should fail

# Test local inference still works
ollama run llama3.2 "Hello, are you working offline?"
```

### 3. Context Management
- Use the context-simple module for efficient prompt management
- Keep conversations focused to work within local model context limits
- Clear context periodically for fresh sessions

### 4. Storage Management
```bash
# Check storage usage
du -sh ~/.ollama/models/
du -sh ~/whisper.cpp/models/

# Remove unused models to free space
ollama rm unused-model-name
```

---

## Troubleshooting

### Model Not Loading
- Check available RAM: `free -h`
- Try a smaller model
- Close other applications

### Slow Inference
- Enable GPU acceleration if available
- Use a smaller/quantized model
- Reduce context length in settings

### STT Not Working
- Verify whisper.cpp is compiled: `./main --help`
- Check model path is correct
- Ensure audio input is working: `arecord -l`

---

## Privacy Verification Checklist

- [ ] Network disconnected or firewall blocking outbound
- [ ] No cloud API keys configured
- [ ] Local storage module active (SQLite)
- [ ] Models stored locally (not streamed)
- [ ] Telemetry disabled in all components

**Your data never leaves your machine.**
