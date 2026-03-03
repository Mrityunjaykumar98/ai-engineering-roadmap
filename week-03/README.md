# Week 3: Transformer Architecture Internals

> **Goal:** Dive deep into LLM internals — QKV matrices, Cross Attention, Multi-head Attention, Feed Forward Neural Networks, and Logits.

---

## 📋 Topics Covered

- **Q, K, V Matrices** — The mechanics of attention
- **Cross Attention** — How encoder and decoder communicate
- **Multi-head Attention** — Parallel attention for richer representations
- **Feed Forward Neural Networks (FFNNs)** — The "thinking" layers
- **Logits** — How the model produces its final output

---

## 🗺️ Learning Path

### Step 1: Q, K, V Matrices — Deep Dive

The attention mechanism computes three matrices from the input: **Query (Q)**, **Key (K)**, and **Value (V)**. Think of it like a library:
- **Query:** "What am I looking for?"
- **Key:** "What do I contain?"
- **Value:** "Here's my actual content"

The computation: `Attention(Q, K, V) = softmax(QK^T / √d_k) × V`

| Resource | Type | Duration | Link |
|---|---|---|---|
| QKV Attention Explained Visually | 📹 Video | 20min | [Watch](https://www.youtube.com/watch?v=ISNdQcPhsts) |
| Illustrated GPT-2 — Jay Alammar | 📖 Blog | ~1h | [Read](https://jalammar.github.io/illustrated-gpt2/) |
| The Annotated Transformer (Harvard NLP) | 💻 Code + Tutorial | ~2h | [Read](https://nlp.seas.harvard.edu/annotated-transformer/) |
| Lilian Weng — The Transformer Family v2 | 📖 Blog | ~1h | [Read](https://lilianweng.github.io/posts/2023-01-27-the-transformer-family-v2/) |

---

### Step 2: Cross Attention

Cross attention is how the **decoder** attends to the **encoder's** output. In an encoder-decoder model (like T5 or the original Transformer):
- Self-attention: tokens attend to each other within the same sequence
- Cross-attention: decoder tokens attend to encoder output (different sequences)

**Where it's used:**
- Original Transformer (machine translation)
- T5, BART
- Stable Diffusion (text conditions the image generation via cross-attention)

| Resource | Type | Duration | Link |
|---|---|---|---|
| Cross Attention Explained | 📹 Video | 15min | [Watch](https://www.youtube.com/watch?v=KGPZM3prq_8) |
| Encoder-Decoder vs Decoder-only | 📖 Blog | ~20min | [Read](https://magazine.sebastianraschka.com/p/understanding-encoder-and-decoder) |
| Illustrated BERT — Jay Alammar | 📖 Blog | ~30min | [Read](https://jalammar.github.io/illustrated-bert/) |

---

### Step 3: Multi-Head Attention

Instead of computing attention once, multi-head attention runs it **in parallel N times** with different learned projections, then concatenates the results.

**Why multiple heads?**
- Different heads can learn different types of relationships
- Head 1 might learn syntactic relationships ("subject-verb")
- Head 2 might learn positional patterns ("nearby words")
- Head 3 might learn semantic similarity

Typically: 8 heads (BERT-base), 12 heads (BERT-large), 32 heads (GPT-3), 96 heads (GPT-4)

| Resource | Type | Duration | Link |
|---|---|---|---|
| Multi-Head Attention — Umar Jamil | 📹 Video | 30min | [Watch](https://www.youtube.com/watch?v=ISNdQcPhsts) |
| Transformers from Scratch — Peter Bloem | 📖 Blog | ~1.5h | [Read](https://peterbloem.nl/blog/transformers) |
| Attention Head Visualization — BertViz | 💻 Tool | N/A | [Try](https://github.com/jessevig/bertviz) |

---

### Step 4: Feed Forward Neural Networks (FFNNs)

After the attention layer, every token passes through a **position-wise feed-forward network** — two linear transformations with a ReLU/GELU activation in between.

```
FFN(x) = max(0, xW₁ + b₁)W₂ + b₂
```

**Why it matters:**
- The FFNN layers contain most of the model's parameters (~⅔ in GPT-3)
- They act as "fact storage" — individual neurons encode specific knowledge
- The attention layers decide WHAT to look at; the FFNNs decide WHAT TO DO with it

| Resource | Type | Duration | Link |
|---|---|---|---|
| Transformer Feed Forward Layers Are Key-Value Memories | 📄 Paper | ~45min | [Read](https://arxiv.org/abs/2012.14913) |
| The Annotated Transformer — FFNN section | 💻 Code | ~20min | [Read](https://nlp.seas.harvard.edu/annotated-transformer/) |

---

### Step 5: Logits & Output Layer

The final layer of an LLM produces **logits** — raw, unnormalized scores for every token in the vocabulary. These get converted to probabilities via softmax.

**Key concepts:**
- **Logits:** Raw output scores (one per vocab token)
- **Softmax:** Converts logits to probability distribution
- **Temperature:** Controls randomness. Low temp → confident/repetitive. High temp → creative/random
- **Top-k / Top-p sampling:** Strategies for choosing the next token
- **Greedy decoding vs. sampling:** Deterministic vs. probabilistic output

| Resource | Type | Duration | Link |
|---|---|---|---|
| How GPT Generates Text — Jay Alammar | 📖 Blog | ~30min | [Read](https://jalammar.github.io/illustrated-gpt2/) |
| Text Generation Strategies — HuggingFace | 📖 Docs | ~20min | [Read](https://huggingface.co/blog/how-to-generate) |
| Temperature, Top-k, Top-p Explained | 📹 Video | 15min | [Watch](https://www.youtube.com/watch?v=YjVWJahgWI4) |

---

## 🧪 Practice Exercises

1. **Annotated Transformer:** Work through the [Harvard NLP Annotated Transformer](https://nlp.seas.harvard.edu/annotated-transformer/) and run each code cell.

2. **Attention from Scratch:** Implement scaled dot-product attention and multi-head attention in PyTorch (no library calls).

3. **Logits Explorer:** Load a pre-trained GPT-2 from HuggingFace, feed it a prompt, and examine the raw logits. Try different temperature/top-k settings and see how outputs change.

---

## ✅ Week 3 Checklist

- [ ] Deeply understand Q, K, V computation (be able to explain it to someone)
- [ ] Understand difference between self-attention and cross-attention
- [ ] Know why multi-head attention is better than single-head
- [ ] Understand the role of FFNNs in transformers
- [ ] Know what logits are and how sampling strategies work
- [ ] Work through the Annotated Transformer
- [ ] Push notes/code to `week-03/`

---

**⬅️ Previous: [Week 2: Tokenization, Vectorization & Attention](../week-02/README.md)**
**➡️ Next: [Week 4: Causal Attention + Coding a Transformer](../week-04/README.md)**
