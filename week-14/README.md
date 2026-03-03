# Week 14: Diffusion Based Models

> **Goal:** Learn the internals of diffusion-based models and why they are overtaking transformer architectures for image and video generation.

---

## 📋 Topics Covered

- **Diffusion Architecture** — How noise becomes art
- **Text-based Diffusion** — Connecting language to image generation
- **Image and Video Generation**
- **Diffusion Models vs LLMs**

---

## 🗺️ Learning Path

### Step 1: How Diffusion Models Work

Diffusion models learn to generate images by reversing a noise-adding process.

**Forward process (training):** Gradually add Gaussian noise to an image until it's pure noise
**Reverse process (generation):** Start from pure noise and gradually remove noise to create an image

```
Image → Add noise step by step → Pure noise
Pure noise → Remove noise step by step → New image
```

The model learns a **denoising function** — given a noisy image and a timestep, predict the noise that was added.

| Resource | Type | Duration | Link |
|---|---|---|---|
| What Are Diffusion Models? — Lilian Weng | 📖 Blog | ~1h | [Read](https://lilianweng.github.io/posts/2021-07-11-diffusion-models/) |
| Illustrated Stable Diffusion — Jay Alammar | 📖 Blog | ~45min | [Read](https://jalammar.github.io/illustrated-stable-diffusion/) |
| How AI Image Generators Work — Computerphile | 📹 Video | 20min | [Watch](https://www.youtube.com/watch?v=1CIpzeNxIhU) |
| Diffusion Models — Yang Song (Stanford) | 📹 Video | 1h | [Watch](https://www.youtube.com/watch?v=687zEGODmHA) |
| DDPM Paper — Ho et al. | 📄 Paper | ~1h | [Read](https://arxiv.org/abs/2006.11239) |

---

### Step 2: Stable Diffusion Architecture

Stable Diffusion is the most popular open-source image generation model. It works in **latent space** rather than pixel space, making it much faster.

**Architecture components:**
1. **VAE Encoder:** Compresses image from pixel space → latent space
2. **U-Net (Denoiser):** Predicts and removes noise in latent space
3. **Text Encoder (CLIP):** Converts text prompt → conditioning embedding
4. **VAE Decoder:** Converts denoised latent → final image
5. **Scheduler:** Controls the noise schedule (DDPM, DDIM, Euler, etc.)

| Resource | Type | Duration | Link |
|---|---|---|---|
| Stable Diffusion Deep Dive — Umar Jamil | 📹 Video | 1h | [Watch](https://www.youtube.com/watch?v=HoKDTa5jHvg) |
| High-Resolution Image Synthesis (LDM Paper) | 📄 Paper | ~1h | [Read](https://arxiv.org/abs/2112.10752) |
| HuggingFace Diffusers — Getting Started | 📖 Docs | ~30min | [Start](https://huggingface.co/docs/diffusers/en/index) |
| Diffusion Models Course — HuggingFace (Free) | 📚 Course | ~4h | [Start](https://huggingface.co/learn/diffusion-course/en/unit1/1) |
| Stable Diffusion from Scratch — Code | 💻 Code | Reference | [GitHub](https://github.com/hkproj/pytorch-stable-diffusion) |

> **📄 Research Paper:** [Denoising Diffusion Probabilistic Models — Ho et al., 2020](https://arxiv.org/abs/2006.11239) — The foundational diffusion paper.

---

### Step 3: Text-to-Image and Beyond

**Key techniques:**
- **Classifier-Free Guidance (CFG):** Balance between prompt adherence and image quality
- **ControlNet:** Add spatial control (pose, edges, depth) to generation
- **DreamBooth:** Fine-tune on a few images of a specific subject
- **LoRA for Diffusion:** Lightweight fine-tuning for style/concept learning
- **Inpainting/Outpainting:** Edit specific parts of an image

| Resource | Type | Duration | Link |
|---|---|---|---|
| Classifier-Free Guidance Explained | 📖 Blog | ~20min | [Read](https://sander.ai/2022/05/26/guidance.html) |
| ControlNet Paper | 📄 Paper | ~30min | [Read](https://arxiv.org/abs/2302.05543) |
| DreamBooth Paper | 📄 Paper | ~30min | [Read](https://arxiv.org/abs/2208.12242) |
| ComfyUI (Node-based SD workflow) | 💻 Open Source | Reference | [GitHub](https://github.com/comfyanonymous/ComfyUI) |

---

### Step 4: Diffusion Models vs LLMs

| Aspect | Diffusion Models | LLMs |
|---|---|---|
| **Output** | Images/Video (continuous) | Text (discrete tokens) |
| **Generation** | Iterative denoising (many steps) | Auto-regressive (one token at a time) |
| **Training** | Predict noise at each timestep | Predict next token |
| **Architecture** | U-Net / DiT (Diffusion Transformer) | Decoder-only Transformer |
| **Conditioning** | Cross-attention with text embeddings | Text-in, text-out |

**Emerging trend: Diffusion Transformers (DiT)**
- Replace U-Net with a Transformer backbone
- Used by Sora, FLUX, Stable Diffusion 3
- Suggests convergence of both paradigms

| Resource | Type | Duration | Link |
|---|---|---|---|
| DiT Paper — Scalable Diffusion with Transformers | 📄 Paper | ~30min | [Read](https://arxiv.org/abs/2212.09748) |
| FLUX Architecture Explained | 📹 Video | 20min | [Watch](https://www.youtube.com/watch?v=_eTG4EUqXjU) |

---

## 🧪 Practice Exercise

1. **Generate images** with Stable Diffusion using HuggingFace Diffusers on Colab
2. **Experiment** with different schedulers, CFG scales, and step counts
3. **Try ControlNet** for guided generation
4. **Fine-tune with DreamBooth** on 5 photos of an object

---

## ✅ Week 14 Checklist

- [ ] Understand the forward and reverse diffusion process
- [ ] Know the Stable Diffusion architecture (VAE + U-Net + CLIP)
- [ ] Generate images using the Diffusers library
- [ ] Understand how text conditions the image generation
- [ ] Know the differences between diffusion models and LLMs
- [ ] Push your experiments to `week-14/`

---

**⬅️ Previous: [Week 13: Image and Video Models](../week-13/README.md)**
**➡️ Next: [Week 15: Capstone Project](../week-15/README.md)**
