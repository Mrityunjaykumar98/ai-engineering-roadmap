# Week 6: Quantization and Fine-Tuning

> **Goal:** Learn how LLMs are quantized for fast processing and how to fine-tune models to meet specific business requirements.

---

## 📋 Topics Covered

- **KV Cache** — Speeding up inference
- **Quantization** — FP16, INT8, INT4, attention optimizations
- **Fine-Tuning** — LoRA, QLoRA
- **Dataset Prep → Training → Evaluation**

---

## 🗺️ Learning Path

### Step 1: KV Cache

During auto-regressive generation, the model recomputes attention for ALL previous tokens at every step. The KV cache stores previously computed Key and Value tensors to avoid redundant computation.

**Without KV cache:** O(n²) per token generation
**With KV cache:** O(n) per token generation

| Resource | Type | Duration | Link |
|---|---|---|---|
| KV Cache Explained — Medium | 📖 Article | ~15min | [Read](https://medium.com/@joaolages/kv-caching-explained-276520203249) |
| KV Cache Illustrated | 📹 Video | 15min | [Watch](https://www.youtube.com/watch?v=80bIUggRJf4) |
| Efficient Transformers Survey — Google | 📄 Paper | ~1h | [Read](https://arxiv.org/abs/2009.06732) |

---

### Step 2: Quantization

Quantization reduces model size and speeds up inference by using lower-precision numbers.

**Key concepts:**
- **FP32 → FP16 → INT8 → INT4:** Each step halves the memory
- **Post-training quantization (PTQ):** Quantize after training — fast but some accuracy loss
- **Quantization-aware training (QAT):** Train with quantization in mind — better quality
- **GGUF:** Popular format for running quantized models locally (llama.cpp)
- **GPTQ, AWQ, GGML:** Different quantization algorithms with different tradeoffs
- **Flash Attention:** Memory-efficient attention computation

| Resource | Type | Duration | Link |
|---|---|---|---|
| Quantization Fundamentals — HuggingFace | 📖 Docs | ~30min | [Read](https://huggingface.co/docs/optimum/concept_guides/quantization) |
| A Visual Guide to Quantization — Maarten Grootendorst | 📖 Blog | ~30min | [Read](https://newsletter.maartengrootendorst.com/p/a-visual-guide-to-quantization) |
| GGUF & llama.cpp — Run LLMs Locally | 💻 Code | Reference | [GitHub](https://github.com/ggerganov/llama.cpp) |
| Flash Attention Paper | 📄 Paper | ~45min | [Read](https://arxiv.org/abs/2205.14135) |
| TheBloke Models — Pre-quantized | 💻 Models | Reference | [HuggingFace](https://huggingface.co/TheBloke) |

---

### Step 3: Fine-Tuning with LoRA & QLoRA

Full fine-tuning updates ALL model parameters — expensive and requires lots of GPU memory. LoRA/QLoRA make it practical.

**LoRA (Low-Rank Adaptation):**
- Freezes the original model weights
- Adds small trainable matrices (rank decomposition) to attention layers
- Typically only 0.1-1% of original parameters are trained
- Result: Same quality, fraction of the cost

**QLoRA (Quantized LoRA):**
- Combines 4-bit quantization + LoRA
- Fine-tune a 70B model on a single GPU!
- Uses double quantization and paged optimizers

| Resource | Type | Duration | Link |
|---|---|---|---|
| LoRA Explained — Sebastian Raschka | 📖 Blog | ~30min | [Read](https://magazine.sebastianraschka.com/p/lora-and-dora-from-scratch) |
| QLoRA Paper | 📄 Paper | ~45min | [Read](https://arxiv.org/abs/2305.14314) |
| Fine-tune LLMs with HuggingFace (Practical) | 📖 Tutorial | ~1h | [Read](https://huggingface.co/docs/trl/en/sft_trainer) |
| Fine-tune Llama 3 with QLoRA — Free Colab | 📹 Video + 💻 | 1h | [Watch](https://www.youtube.com/watch?v=aQmoog_s8HE) |
| PEFT Library — HuggingFace | 📖 Docs | Reference | [Read](https://huggingface.co/docs/peft/en/index) |
| Unsloth — 2x Faster Fine-tuning | 💻 Tools | Reference | [GitHub](https://github.com/unslothai/unsloth) |

> **📄 Research Paper:** [LoRA: Low-Rank Adaptation of Large Language Models — Hu et al., 2021](https://arxiv.org/abs/2106.09685)

---

### Step 4: Dataset Preparation & Training Pipeline

**The fine-tuning pipeline:**
1. **Collect/curate data** — instruction-response pairs
2. **Format data** — Alpaca format, ShareGPT format, or chat templates
3. **Tokenize** — Convert to model's expected format
4. **Train** — LoRA/QLoRA with proper hyperparameters
5. **Evaluate** — Compare fine-tuned vs. base model performance
6. **Merge & export** — Merge LoRA weights back into base model

| Resource | Type | Duration | Link |
|---|---|---|---|
| Alpaca Dataset Format | 💻 Dataset | Reference | [HuggingFace](https://huggingface.co/datasets/tatsu-lab/alpaca) |
| Creating Good Training Data | 📖 Blog | ~20min | [Read](https://magazine.sebastianraschka.com/p/tips-for-llm-pretraining-and-evaluating-rms) |
| Axolotl — Fine-tuning Framework | 💻 Code | Reference | [GitHub](https://github.com/axolotl-ai-cloud/axolotl) |

---

## 🧪 Coding Assignment

### Fine-tune a small LLM using QLoRA

1. Choose a base model (Phi-3-mini, Llama-3-8B, or Mistral-7B)
2. Prepare a small instruction dataset (or use an existing one)
3. Fine-tune using QLoRA on Google Colab (free T4 GPU)
4. Compare outputs before and after fine-tuning
5. Export the model in GGUF format and run it locally

### Stretch Goals:
- [ ] Fine-tune on your own custom dataset
- [ ] Try different LoRA ranks (r=8, 16, 32) and compare
- [ ] Evaluate using MMLU or other benchmarks
- [ ] Use Unsloth for faster training

---

## ✅ Week 6 Checklist

- [ ] Understand KV cache and why it speeds up inference
- [ ] Know the quantization landscape (FP16, INT8, INT4, GGUF)
- [ ] Understand LoRA and QLoRA intuitively
- [ ] Fine-tune a model on Colab using QLoRA
- [ ] Push your fine-tuning code to `week-06/`

---

**⬅️ Previous: [Week 5: LLM Training at Scale](../week-05/README.md)**
**➡️ Next: [Week 7: Retrieval Augmented Generation](../week-07/README.md)**
