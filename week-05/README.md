# Week 5: LLM Training at Scale

> **Goal:** Learn the end-to-end lifecycle of an LLM — from data processing to pre-training, post-training, and evaluation.

---

## 📋 Topics Covered

- **End-to-end LLM Lifecycle** — From raw data to deployed model
- **Pre-training** — Massive-scale unsupervised training
- **Post-training** — SFT, RLHF, DPO
- **Model Evaluation** — Benchmarks and metrics

---

## 🗺️ Learning Path

### Step 1: The LLM Lifecycle

```
Raw Data → Cleaning → Tokenization → Pre-training → Post-training (SFT + RLHF) → Evaluation → Deployment
```

| Resource | Type | Duration | Link |
|---|---|---|---|
| Building LLM Applications — Chip Huyen | 📖 Blog | ~1h | [Read](https://huyenchip.com/2023/04/11/llm-engineering.html) |
| How ChatGPT is Trained — Andrej Karpathy (Intro) | 📹 Video | 1h | [Watch](https://www.youtube.com/watch?v=bZQun8Y4L2A) |
| LLM University — Cohere (Full Course) | 📚 Course | Self-paced | [Start](https://cohere.com/llmu) |
| State of GPT — Andrej Karpathy (Microsoft Build) | 📹 Video | 45min | [Watch](https://www.youtube.com/watch?v=bZQun8Y4L2A) |

---

### Step 2: Pre-training

Pre-training is the most expensive phase. The model learns language by predicting the next token on trillions of tokens of text.

**Key concepts:**
- **Training data:** Web crawls (C4, The Pile, RefinedWeb), books, code
- **Data quality:** Deduplication, filtering, toxicity removal
- **Training objective:** Next-token prediction (causal LM)
- **Distributed training:** Data parallelism, model parallelism, pipeline parallelism
- **Hardware:** Thousands of GPUs/TPUs for weeks/months

| Resource | Type | Duration | Link |
|---|---|---|---|
| The Pile Dataset Paper | 📄 Paper | ~30min | [Read](https://arxiv.org/abs/2101.00027) |
| Llama 2 Technical Report | 📄 Paper | ~1h | [Read](https://arxiv.org/abs/2307.09288) |
| Distributed Training — HuggingFace | 📖 Docs | ~30min | [Read](https://huggingface.co/docs/transformers/perf_train_gpu_many) |
| How to Train Really Large Models — Lilian Weng | 📖 Blog | ~1h | [Read](https://lilianweng.github.io/posts/2021-09-25-train-large/) |

---

### Step 3: Post-training (SFT + RLHF)

After pre-training, the model knows language but doesn't follow instructions well. Post-training aligns it with human preferences.

**Supervised Fine-tuning (SFT):**
- Train on high-quality instruction-response pairs
- "Be helpful, harmless, and honest"

**RLHF (Reinforcement Learning from Human Feedback):**
- Humans rank model outputs
- Train a reward model on human preferences
- Use PPO to optimize the LLM against the reward model

**DPO (Direct Preference Optimization):**
- Simpler alternative to RLHF — no separate reward model needed
- Directly optimizes for human preferences

| Resource | Type | Duration | Link |
|---|---|---|---|
| RLHF Explained — HuggingFace | 📖 Blog | ~30min | [Read](https://huggingface.co/blog/rlhf) |
| InstructGPT Paper (RLHF origins) | 📄 Paper | ~1h | [Read](https://arxiv.org/abs/2203.02155) |
| DPO Paper — Direct Preference Optimization | 📄 Paper | ~45min | [Read](https://arxiv.org/abs/2305.18290) |
| RLHF Illustrated — Chip Huyen | 📖 Blog | ~30min | [Read](https://huyenchip.com/2023/05/02/rlhf.html) |

---

### Step 4: Model Evaluation

**Benchmarks:**
- **MMLU:** Massive Multitask Language Understanding (general knowledge)
- **HumanEval:** Code generation benchmark
- **GSM8K:** Grade school math reasoning
- **ARC:** Science reasoning
- **TruthfulQA:** Measuring hallucinations
- **MT-Bench:** Multi-turn conversation quality

| Resource | Type | Duration | Link |
|---|---|---|---|
| HELM Benchmark — Stanford | 📖 Resource | Reference | [Visit](https://crfm.stanford.edu/helm/latest/) |
| Open LLM Leaderboard — HuggingFace | 📖 Resource | Reference | [Visit](https://huggingface.co/spaces/open-llm-leaderboard/open_llm_leaderboard) |
| Chatbot Arena (LMSYS) | 📖 Resource | Reference | [Visit](https://lmarena.ai/) |
| Evaluating LLMs — A Practical Guide | 📖 Blog | ~30min | [Read](https://www.confident-ai.com/blog/llm-evaluation-metrics-everything-you-need-for-llm-evaluation) |

---

## ✅ Week 5 Checklist

- [ ] Understand the full LLM training pipeline (data → pre-train → post-train → eval)
- [ ] Read the Llama 2 technical report
- [ ] Understand SFT, RLHF, and DPO
- [ ] Explore the Open LLM Leaderboard and model benchmarks
- [ ] Push your notes to `week-05/`

---

**⬅️ Previous: [Week 4: Causal Attention + Coding a Transformer](../week-04/README.md)**
**➡️ Next: [Week 6: Quantization and Fine-Tuning](../week-06/README.md)**
