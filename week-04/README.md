# Week 4: Causal Attention + Coding a Transformer

> **Goal:** Code the internals of a transformer from scratch, following the "Attention is All You Need" architecture.

---

## 📋 Topics Covered

- **Causal Masked Attention** — How decoder-only models prevent "looking ahead"
- **Model Training** — How transformers learn via next-token prediction
- **Auto-regressive Generation** — How text is generated token by token
- **🧪 Coding Assignment:** Implement a Transformer from scratch

---

## 🗺️ Learning Path

### Step 1: Causal (Masked) Attention

In decoder-only models (GPT), each token can only attend to **previous tokens** — never future ones. This is enforced with a **causal mask** (lower-triangular matrix of 1s).

**Why it matters:**
- Without causal masking, the model would "cheat" during training by seeing the answer
- This is what makes GPT a "left-to-right" language model
- The mask is the key difference between BERT (bidirectional) and GPT (causal)

```
Attention mask for 4 tokens:
[1, 0, 0, 0]   ← token 1 sees only itself
[1, 1, 0, 0]   ← token 2 sees tokens 1-2
[1, 1, 1, 0]   ← token 3 sees tokens 1-3
[1, 1, 1, 1]   ← token 4 sees all tokens
```

| Resource | Type | Duration | Link |
|---|---|---|---|
| Let's build GPT from Scratch — Karpathy | 📹 Video | 2h | [Watch](https://www.youtube.com/watch?v=kCc8FmEb1nY) |
| Causal vs Bidirectional Attention | 📖 Blog | ~20min | [Read](https://magazine.sebastianraschka.com/p/understanding-encoder-and-decoder) |
| nanoGPT — Full Codebase | 💻 Code | Reference | [GitHub](https://github.com/karpathy/nanoGPT) |

---

### Step 2: Auto-regressive Generation

LLMs generate text one token at a time, feeding each generated token back as input:

```
Input:  "The cat"
Step 1: "The cat" → model → "sat"
Step 2: "The cat sat" → model → "on"
Step 3: "The cat sat on" → model → "the"
...
```

**Key concepts:**
- **Teacher forcing:** During training, use ground-truth tokens (not model's own predictions)
- **KV Cache:** Stores previous keys/values to avoid recomputation during generation
- **Stopping criteria:** EOS token, max length, or other conditions

| Resource | Type | Duration | Link |
|---|---|---|---|
| Auto-regressive Models Explained | 📹 Video | 15min | [Watch](https://www.youtube.com/watch?v=IGu7ivuy1Ag) |
| Text Generation Strategies — HuggingFace | 📖 Docs | ~20min | [Read](https://huggingface.co/blog/how-to-generate) |

---

### Step 3: Code a Transformer from Scratch

This is the core assignment for this week. You should be able to implement the full transformer architecture in PyTorch.

**Implementation order:**
1. Token + Positional Embeddings
2. Scaled Dot-Product Attention
3. Multi-Head Attention
4. Feed-Forward Network
5. Transformer Block (LayerNorm + Attention + FFN + Residual connections)
6. Full GPT Model (stack of Transformer blocks + output head)
7. Training loop with next-token prediction loss

| Resource | Type | Duration | Link |
|---|---|---|---|
| Let's build GPT — Karpathy (THE resource) | 📹 Video | 2h | [Watch](https://www.youtube.com/watch?v=kCc8FmEb1nY) |
| LLMs from Scratch — Sebastian Raschka | 💻 Book + Code | ~4h | [GitHub](https://github.com/rasbt/LLMs-from-scratch) |
| Coding a Transformer — Umar Jamil | 📹 Video | 1.5h | [Watch](https://www.youtube.com/watch?v=ISNdQcPhsts) |
| minGPT — Karpathy | 💻 Code | Reference | [GitHub](https://github.com/karpathy/minGPT) |
| The Annotated Transformer — Harvard NLP | 💻 Code + Tutorial | ~2h | [Read](https://nlp.seas.harvard.edu/annotated-transformer/) |

> **📄 Research Paper:** [Attention Is All You Need — Vaswani et al., 2017](https://arxiv.org/abs/1706.03762) — Read it alongside your implementation. Map every section of the paper to your code.

> **📄 Research Paper:** [Language Models are Unsupervised Multitask Learners (GPT-2) — Radford et al., 2019](https://cdn.openai.com/better-language-models/language_models_are_unsupervised_multitask_learners.pdf) — Understand GPT-2's decoder-only approach.

---

## 🧪 Coding Assignment

### Build a character-level GPT

Follow Karpathy's "Let's build GPT" video to build a character-level language model:

1. Train on Shakespeare's text (or any text corpus)
2. Implement all transformer components from scratch
3. Generate new text that "sounds like" Shakespeare

### Stretch Goals:
- [ ] Train on a different corpus (song lyrics, code, recipes)
- [ ] Experiment with different model sizes (heads, layers, embedding dim)
- [ ] Add learning rate scheduling (warmup + cosine decay)
- [ ] Compare character-level vs. BPE tokenization

---

## ✅ Week 4 Checklist

- [ ] Watch Karpathy's "Let's build GPT" (code along from scratch!)
- [ ] Understand causal masking and auto-regressive generation
- [ ] Implement a complete transformer in PyTorch
- [ ] Train your model and generate text
- [ ] Read the GPT-2 paper
- [ ] Push your implementation to `week-04/`

---

**⬅️ Previous: [Week 3: Transformer Architecture Internals](../week-03/README.md)**
**➡️ Next: [Week 5: LLM Training at Scale](../week-05/README.md)**
