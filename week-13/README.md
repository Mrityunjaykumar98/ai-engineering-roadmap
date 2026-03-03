# Week 13: Image and Video Models

> **Goal:** Learn how multimodal models are trained with images and video, and the mechanism of diffusion-based models.

---

## 📋 Topics Covered

- **GANs** — Generative Adversarial Networks
- **Multimodal Models** — Vision + Language
- **CLIP** — Connecting text and images
- **Video Models**

---

## 🗺️ Learning Path

### Step 1: GANs (Generative Adversarial Networks)

GANs were the dominant image generation architecture before diffusion models. Understanding them helps appreciate the evolution.

**How GANs work:**
- **Generator:** Creates fake images trying to fool the discriminator
- **Discriminator:** Tries to distinguish real images from fake ones
- They train adversarially — each pushing the other to improve
- Result: The generator learns to produce realistic images

**Notable GANs:** DCGAN, StyleGAN, CycleGAN, Pix2Pix

| Resource | Type | Duration | Link |
|---|---|---|---|
| GANs from Scratch — Goodfellow lecture | 📹 Video | 1h | [Watch](https://www.youtube.com/watch?v=9JpdAg6uMXs) |
| StyleGAN Explained | 📹 Video | 25min | [Watch](https://www.youtube.com/watch?v=kSLJriaOumA) |
| GAN Lab Interactive Visualization | 🧪 Interactive | N/A | [Try](https://poloclub.github.io/ganlab/) |
| GAN Paper — Original | 📄 Paper | ~30min | [Read](https://arxiv.org/abs/1406.2661) |
| This Person Does Not Exist | 🧪 Demo | N/A | [See](https://thispersondoesnotexist.com/) |

---

### Step 2: Multimodal Models

Multimodal models understand and generate across different modalities — text, images, audio, video.

**Key architectures:**
- **Vision Transformers (ViT):** Apply transformer architecture to image patches
- **LLaVA:** LLM + Vision encoder for visual question answering
- **Gemini/GPT-4V:** Native multimodal from the ground up
- **Flamingo:** Few-shot visual question answering

| Resource | Type | Duration | Link |
|---|---|---|---|
| Vision Transformers (ViT) Explained | 📹 Video | 30min | [Watch](https://www.youtube.com/watch?v=TrdevFK_am4) |
| ViT Paper | 📄 Paper | ~45min | [Read](https://arxiv.org/abs/2010.11929) |
| LLaVA Paper — Visual Instruction Tuning | 📄 Paper | ~30min | [Read](https://arxiv.org/abs/2304.08485) |
| Multimodal LLMs Explained — Umar Jamil | 📹 Video | 40min | [Watch](https://www.youtube.com/watch?v=vAmKB7iPkWw) |
| Build a Multimodal App — Google AI Studio | 📖 Tutorial | ~30min | [Start](https://ai.google.dev/gemini-api/docs/vision) |

---

### Step 3: CLIP — Connecting Vision and Language

CLIP (Contrastive Language-Image Pre-training) by OpenAI is a breakthrough model that learns to connect text and images in a shared embedding space.

**How CLIP works:**
- Train on 400M (image, text) pairs from the internet
- Image encoder → image embedding
- Text encoder → text embedding
- Training objective: match correct image-text pairs, push incorrect ones apart
- Result: Can classify images using text descriptions without fine-tuning

**Applications:** Image search, zero-shot classification, image generation guidance (used by DALL-E and Stable Diffusion)

| Resource | Type | Duration | Link |
|---|---|---|---|
| CLIP Paper — OpenAI | 📄 Paper | ~1h | [Read](https://arxiv.org/abs/2103.00020) |
| CLIP Explained — Yannic Kilcher | 📹 Video | 30min | [Watch](https://www.youtube.com/watch?v=T9XSU0pKX2E) |
| OpenCLIP — Open Source Implementation | 💻 Code | Reference | [GitHub](https://github.com/mlfoundations/open_clip) |
| CLIP Tutorial — HuggingFace | 📖 Docs | ~20min | [Read](https://huggingface.co/docs/transformers/model_doc/clip) |

---

### Step 4: Video Models

Video understanding and generation is the next frontier in AI.

**Key approaches:**
- **Video as sequence of frames:** Apply image models per frame + temporal modeling
- **Video Transformers:** ViViT, TimeSformer — extend ViT to video
- **Video Generation:** Sora, Runway Gen-3, Kling — generate video from text

| Resource | Type | Duration | Link |
|---|---|---|---|
| Sora Technical Report — OpenAI | 📄 Paper | ~30min | [Read](https://openai.com/research/video-generation-models-as-world-simulators) |
| Video Understanding Survey | 📄 Paper | ~45min | [Read](https://arxiv.org/abs/2405.08222) |
| Runway ML Research | 📖 Research | Reference | [Visit](https://research.runwayml.com/) |

---

## ✅ Week 13 Checklist

- [ ] Understand how GANs work (generator vs discriminator)
- [ ] Know what Vision Transformers are and how they process images
- [ ] Understand CLIP's contrastive training approach
- [ ] Have a high-level understanding of video models
- [ ] Try building a simple image classification with CLIP
- [ ] Push your notes/code to `week-13/`

---

**⬅️ Previous: [Week 12: Reasoning Models](../week-12/README.md)**
**➡️ Next: [Week 14: Diffusion Based Models](../week-14/README.md)**
