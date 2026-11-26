# LLMFit RTX 2060 Super + 32GB DDR4

Best uncensored/Heretic LLM models optimized for your RTX 2060 Super + 32GB DDR4 hardware.

## Overview

This website compares the top 10 best uncensored/Heretic LLM models for your specific GPU configuration, including:
- Performance benchmarks (tokens/second)
- VRAM requirements
- Context window support
- llama.cpp launch commands
- Method descriptions (Abliteration, Heretic, Fine-tuning)

## Features

- **10 Top Models**: From lightweight (4B-2B active) to large (40B) models
- **Speed Comparison**: GPU inference speeds from 20-100+ tokens/second
- **VRAM Optimization**: Quantization recommendations for Q4/Q5
- **Heretic Models**: Automatic censorship removal with minimal quality loss
- **Abliterated Models**: Layer-by-layer parameter removal for reduced refusals
- **Direct llama.cpp Commands**: Copy-paste ready launch parameters

## Hardware Requirements

- **GPU**: NVIDIA RTX 2060 Super (8GB VRAM)
- **System RAM**: 32GB DDR4
- **OS**: Windows 10/11 or Linux
- **Software**: llama.cpp (v0.0.20+)

## Quick Start

### Using Docker

```bash
# Build and run
docker-compose up --build

# Access the website
# Open http://localhost:8080 in your browser
```

### Running Models Locally

1. **Download GGUF quantizations** from HuggingFace or ModelScope
2. **Clone this repo** to your local directory
3. **Run with optimal parameters** (see llama.cpp commands in the site)

### Recommended Quantizations

| Model | Q4_K_M | Q5_K_M | Q3_K_M |
|-------|--------|--------|--------|
| Qwen3.8 27B | 16-20GB | 14-18GB | 12-16GB |
| Gemma 4 26B-A4B | 12-14GB | 11-13GB | 10-12GB |
| Gemma 4 31B | 24-28GB | 22-26GB | 20-24GB |
| Flint 40B | 24-32GB | 22-30GB | 20-28GB |

## llama.cpp Best Practices

### Optimal Settings for RTX 2060 Super

```bash
python -m llama.cpp serve \
  --model ./model.gguf \
  --port 13378 \
  --n-context 81920 \
  --n-threads 4 \
  --max-tokens 131072 \
  --gpu-layers 45 \
  --tensor-parallel 1 \
  --mmap true
```

### Key Parameters Explained

- `--n-context 81920`: 81K context window (max for 32GB RAM)
- `--n-threads 4`: Optimal for single RTX 2060 Super
- `--max-tokens 131072`: 128K token generation limit
- `--gpu-layers 45`: Maximize GPU usage (adjust based on VRAM)
- `--tensor-parallel 1`: Single GPU (no multi-GPU on your setup)
- `--mmap true`: Memory mapped for faster loading

## Model Descriptions

### 1. Qwen3.8 27B Uncensored
- **Best for**: Overall performance, coding, agent workflows, vision
- **Method**: Abliteration removes ~30 layers to eliminate refusals
- **Refusals**: ~0/100 (near-eliminated)

### 2. Gemma 4 26B-A4B Heretic
- **Best for**: Speed on modest hardware, MoE efficiency
- **Method**: Heretic ARA (Automatic Refusal Ablation)
- **Active Params**: ~4B per token (MoE architecture)
- **Refusals**: 0/465 reported

### 3. Gemma 4 31B Heretic
- **Best for**: Quality on 32GB+ systems
- **Method**: Heretic ARA with minimal quality degradation
- **Refusals**: ~3/100 (very low)

### 4. Dolphin 3.0 Mistral 24B
- **Best for**: General-purpose chat, function calling
- **Method**: Fine-tuned with refusal-free dataset
- **Design**: Apache 2.0 licensed, inherently uncensored

### 5. Flint 40B-A2.5B Heretic
- **Best for**: Large model performance, advanced reasoning
- **Method**: Abliterix + Optuna fine-tuning
- **Active Params**: ~2.5B (efficient MoE)

### 6. Huihui Qwen 3.6 35B-A3B
- **Best for**: Proven, battle-tested model
- **Method**: Abliteration (layers 22-52)
- **Quantization**: Excellent ecosystem available

### 7. Sage-A1.5 Heretic
- **Best for**: Advanced reasoning tasks
- **Method**: Heretic + Abliteration hybrid
- **Architecture**: MoE (35B total, ~3B active)

### 8. GLM-5.3-Flash Abliterated
- **Best for**: Multimodal/vision tasks
- **Method**: Full-layer abliteration
- **Note**: Requires 256GB+ for full model (uses distilled variants)

### 9. Qwen3.5 9B Ultra Heretic
- **Best for**: Lightweight, fast inference
- **Method**: Heretic with minimal quality loss
- **VRAM**: 4-8GB (Q4)
- **Speed**: 80-100+ T/s

### 10. DeepSeek V4.1 Flash Abliterated
- **Best for**: Security research, red teaming, agents
- **Method**: Abliteration of 1017 checkpoint
- **Context**: 1M token support
- **Refusals**: Near-eliminated

## Inspiration

Design philosophy inspired by [ws.shemsou.com](https://ws.shemsou.com):
- Modern, clean UI
- Gradient accents (blue, purple, cyan)
- Glassmorphism effects
- Performance-focused metrics
- Easy-to-use llama.cpp commands

## License

All models listed use their original licenses (mostly Apache 2.0, MIT).

## Contributing

Found a better model or want to add more? Open a pull request!

## Troubleshooting

**Model won't load?**
- Check VRAM requirements
- Try lower quantization (Q3_K_M instead of Q4_K_M)
- Verify GGUF format compatibility

**Low speed?**
- Ensure `--gpu-layers` is set correctly
- Check for CUDA driver issues
- Try different quantization (Q5_K_M may be faster)

**Too many refusals?**
- Try a more aggressive abliteration
- Consider Heretic method instead of Abliteration

## Resources

- [HuggingFace GGUF Models](https://huggingface.co/models?library=gguf)
- [Llama.cpp GitHub](https://github.com/ggerganov/llama.cpp)
- [Heretic Tool](https://github.com/Whitedevil-13/Heretic)
- [Abliteration Method](https://github.com/huihui-ai/Abliteration)

## Docker Commands

```bash
# Build
docker-compose build

# Run in foreground
docker-compose up

# Run in background
docker-compose up -d

# Stop
docker-compose down
```

## Acknowledgments

- **gguf**: Quantization format by @Quantified
- **llama.cpp**: Inference engine by @ggerganov
- **Heretic**: Censorship removal by @Whitedevil-13
- **Design**: Inspired by ws.shemsou.com
