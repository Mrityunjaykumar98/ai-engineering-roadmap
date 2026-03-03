# Week 2: Tokenization, Vectorization & Attention

> **Goal:** Understand the fundamental building blocks of LLMs — how text becomes numbers and how models learn to focus on what matters.

---

## 📋 Topics Covered

- **Tokenization** — How text is split into tokens (BPE, WordPiece, SentencePiece)
- **Vectorization** — Converting tokens into dense vector representations
- **Positional Encodings** — How transformers know word order
- **Attention Mechanism** — The core innovation that powers all modern LLMs

---

## 🗺️ Learning Path

### Step 1: Tokenization

Tokenization is the very first step in any LLM pipeline. Raw text is split into smaller units (tokens) that the model can process. Understanding this deeply is crucial — bad tokenization can break your model.

**Key concepts:**
- **Character-level tokenization:** Simple but creates very long sequences
- **Word-level tokenization:** Intuitive but can't handle unseen words
- **Subword tokenization (BPE):** The sweet spot — GPT uses this. "unhappiness" → ["un", "happiness"]
- **SentencePiece:** Google's tokenizer (used by LLaMA, T5)
- **Byte-Pair Encoding (BPE):** Iteratively merges most frequent character pairs
- **Vocabulary size tradeoffs:** Larger vocab = shorter sequences but bigger embedding matrix

| Resource | Type | Duration | Link |
|---|---|---|---|
| Let's build the GPT Tokenizer — Karpathy | 📹 Video | 2h | [Watch](https://www.youtube.com/watch?v=zduSFxRajkE) |
| HuggingFace NLP Course — Tokenizers | 📚 Interactive | ~1h | [Start](https://huggingface.co/learn/nlp-course/chapter6/1) |
| Tokenizers — How Machines Read | 📹 Video | 15min | [Watch](https://www.youtube.com/watch?v=wjZofJX0v4M) |
| OpenAI Tokenizer Tool (try it live) | 🧪 Tool | N/A | [Try](https://platform.openai.com/tokenizer) |

> **📄 Research Paper:** [Neural Machine Translation of Rare Words with Subword Units (BPE) — Sennrich et al., 2016](https://arxiv.org/abs/1508.07909) — The paper that introduced BPE to NLP.

---

### Step 2: Vectorization & Embeddings

After tokenization, each token needs to be converted into a vector (a list of numbers) that captures its meaning. This is where the magic begins — words with similar meanings end up close together in vector space.

**Key concepts:**
- **One-hot encoding:** Simple but no semantic meaning, very sparse
- **Word2Vec:** First breakthrough — "king - man + woman ≈ queen"
- **GloVe:** Global Vectors — uses co-occurrence statistics
- **Learned embeddings:** Modern LLMs learn their own embeddings during training
- **Embedding dimensions:** Typically 768 (BERT), 4096 (GPT-3), 8192 (GPT-4)

| Resource | Type | Duration | Link |
|---|---|---|---|
| Word2Vec Explained — StatQuest | 📹 Video | 20min | [Watch](https://www.youtube.com/watch?v=viZrOnJclY0) |
| Stanford CS224N — Word Vectors (Lectures 1-2) | 📹 Video | 2h | [Watch](https://www.youtube.com/playlist?list=PLoROMvodv4rMFqRtEuo6SGjY4XbRIVRd4) |
| What are Embeddings? — Vicki Boykis | 📖 Free Book | ~2h | [Read](https://vickiboykis.com/what_are_embeddings/) |
| Illustrated Word2Vec — Jay Alammar | 📖 Blog | ~30min | [Read](https://jalammar.github.io/illustrated-word2vec/) |
| Pinecone — What are Vector Embeddings? | 📖 Article | ~15min | [Read](https://www.pinecone.io/learn/vector-embeddings/) |

> **📄 Research Paper:** [Efficient Estimation of Word Representations in Vector Space (Word2Vec) — Mikolov et al., 2013](https://arxiv.org/abs/1301.3781) — The paper that started the embeddings revolution.

---

### Step 3: Positional Encodings

Transformers process all tokens in parallel (unlike RNNs which process sequentially). This means they have no inherent sense of word order. Positional encodings solve this by injecting position information.

**Key concepts:**
- **Sinusoidal positional encoding:** Original approach from "Attention is All You Need"
- **Learned positional embeddings:** Used in GPT-2, BERT
- **Rotary Position Embeddings (RoPE):** Used in LLaMA, modern LLMs — encodes relative position
- **ALiBi:** Attention with Linear Biases — simpler alternative

| Resource | Type | Duration | Link |
|---|---|---|---|
| Positional Encoding — Machine Learning Mastery | 📖 Article | ~20min | [Read](https://machinelearningmastery.com/a-gentle-introduction-to-positional-encoding-in-transformer-models/) |
| Visual Guide to Positional Encoding | 📖 Blog | ~15min | [Read](https://kazemnejad.com/blog/transformer_architecture_positional_encoding/) |
| RoPE Explained — EleutherAI | 📖 Blog | ~30min | [Read](https://blog.eleuther.ai/rotary-embeddings/) |

---

### Step 4: The Attention Mechanism

**This is the single most important concept in modern AI.** Attention allows the model to "look at" other parts of the input when processing each token. It's what makes "The cat sat on the mat because **it** was tired" correctly associate "it" with "cat."

**Key concepts:**
- **Self-attention:** Each token attends to all other tokens in the sequence
- **Query, Key, Value (Q, K, V):** The three matrices that compute attention
- **Attention scores:** softmax(QK^T / √d_k) — how much each token should "pay attention" to others
- **Scaled dot-product attention:** The core computation
- **Context window:** How many tokens the model can attend to at once

| Resource | Type | Duration | Link |
|---|---|---|---|
| Illustrated Attention — Jay Alammar | 📖 Blog | ~45min | [Read](https://jalammar.github.io/visualizing-neural-machine-translation-mechanics-of-seq2seq-models-with-attention/) |
| Attention? Attention! — Lilian Weng | 📖 Blog | ~1h | [Read](https://lilianweng.github.io/posts/2018-06-24-attention/) |
| Attention in Transformers — 3Blue1Brown | 📹 Video | 25min | [Watch](https://www.youtube.com/watch?v=eMlx5fFNoYc) |
| Stanford CS224N — Attention Lecture | 📹 Video | 1h | [Watch](https://www.youtube.com/watch?v=ptuGllU5SQQ) |
| The Illustrated Transformer — Jay Alammar | 📖 Blog | ~1h | [Read](https://jalammar.github.io/illustrated-transformer/) |

> **📄 Research Paper:** [Attention Is All You Need — Vaswani et al., 2017](https://arxiv.org/abs/1706.03762) — **THE** foundational paper. Read this multiple times throughout the program.

---

## 🧪 Practice Exercises

1. **Tokenizer Explorer:** Use [OpenAI's tokenizer](https://platform.openai.com/tokenizer) to tokenize different texts. Notice how code, different languages, and special characters are tokenized differently.

2. **Build a simple tokenizer:** Implement BPE from scratch following Karpathy's video.

3. **Word2Vec from Scratch:** Implement a simple Skip-gram model in PyTorch on a small text corpus.

4. **Attention Visualization:** Use [BertViz](https://github.com/jessevig/bertviz) to visualize attention patterns in a pre-trained BERT model.

---

## ✅ Week 2 Checklist

- [ ] Watch Karpathy's Tokenizer video (code along!)
- [ ] Understand Word2Vec and how embeddings work
- [ ] Read Jay Alammar's Illustrated Transformer blog
- [ ] Understand the Q, K, V attention computation
- [ ] Read the "Attention is All You Need" paper (at least the first pass)
- [ ] Try the tokenizer tool and attention visualizations
- [ ] Push your notes/code to `week-02/`

---

**⬅️ Previous: [Week 1: Overview of LLMs](../week-01/README.md)**
**➡️ Next: [Week 3: Transformer Architecture Internals](../week-03/README.md)**
