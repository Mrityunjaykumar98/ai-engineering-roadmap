# Week 12: Reasoning Models

> **Goal:** Learn what reasoning models are and how they are trained using RLHF and Chain of Thought.

---

## 📋 Topics Covered

- **Reasoning Models** — o1, DeepSeek R1, and similar
- **RLHF** — Reinforcement Learning from Human Feedback
- **Chain of Thought (CoT)** — Step-by-step reasoning
- **How to Prompt a Reasoning Model**

---

## 🗺️ Learning Path

### Step 1: What Are Reasoning Models?

Reasoning models (like OpenAI's o1, DeepSeek R1) are LLMs specifically trained to "think" before answering. They decompose complex problems into steps internally.

**Key differences from standard LLMs:**
- Spend more compute at **inference time** (thinking longer = better answers)
- Trained with specialized RL techniques to improve reasoning
- Excel at math, logic, coding, and multi-step problems
- Generally slower but more accurate for complex tasks

| Resource | Type | Duration | Link |
|---|---|---|---|
| OpenAI o1 System Card | 📄 Paper | ~30min | [Read](https://openai.com/index/openai-o1-system-card/) |
| DeepSeek R1 Paper | 📄 Paper | ~1h | [Read](https://arxiv.org/abs/2501.12948) |
| Reasoning Models Explained — Yannic Kilcher | 📹 Video | 30min | [Watch](https://www.youtube.com/watch?v=6PEJ96k1kiw) |
| Scaling Compute at Test Time | 📄 Paper | ~30min | [Read](https://arxiv.org/abs/2408.03314) |

---

### Step 2: RLHF Deep Dive

RLHF is the key technique that makes models like ChatGPT helpful and aligned. For reasoning models, RL is used to teach the model to produce better reasoning chains.

**The RLHF Pipeline:**
1. **Supervised Fine-Tuning (SFT):** Train on demonstration data
2. **Reward Model Training:** Humans rank outputs → train a model to predict human preferences
3. **RL Optimization (PPO/DPO):** Optimize the LLM to maximize the reward model's score

**For Reasoning:**
- Reward signal based on correctness of final answer
- Process supervision: reward each reasoning step, not just the final answer
- GRPO (Group Relative Policy Optimization): Used by DeepSeek

| Resource | Type | Duration | Link |
|---|---|---|---|
| RLHF Deep Dive — HuggingFace | 📖 Blog | ~30min | [Read](https://huggingface.co/blog/rlhf) |
| InstructGPT Paper | 📄 Paper | ~1h | [Read](https://arxiv.org/abs/2203.02155) |
| Process Reward Models (Let's Verify Step by Step) | 📄 Paper | ~30min | [Read](https://arxiv.org/abs/2305.20050) |
| TRL — Transformer RL Library | 💻 Open Source | Reference | [GitHub](https://github.com/huggingface/trl) |
| RLHF Illustrated — Chip Huyen | 📖 Blog | ~30min | [Read](https://huyenchip.com/2023/05/02/rlhf.html) |

---

### Step 3: Chain of Thought (CoT)

Chain of Thought prompting makes LLMs reason step-by-step, dramatically improving performance on complex tasks.

**Types:**
- **Zero-shot CoT:** "Let's think step by step"
- **Few-shot CoT:** Provide reasoning examples in the prompt
- **Self-consistency:** Generate multiple reasoning paths, take majority vote
- **Tree of Thought:** Explore branching reasoning paths

| Resource | Type | Duration | Link |
|---|---|---|---|
| Chain of Thought Paper — Wei et al. | 📄 Paper | ~30min | [Read](https://arxiv.org/abs/2201.11903) |
| Tree of Thought Paper | 📄 Paper | ~30min | [Read](https://arxiv.org/abs/2305.10601) |
| Self-Consistency Paper | 📄 Paper | ~30min | [Read](https://arxiv.org/abs/2203.11171) |
| CoT Prompting Guide — Learn Prompting | 📖 Tutorial | ~15min | [Read](https://learnprompting.org/docs/intermediate/chain_of_thought) |

---

### Step 4: Prompting Reasoning Models

Reasoning models behave differently from standard LLMs — they need different prompting strategies.

**Best practices:**
- **Don't say "think step by step"** — they already do this internally
- **Be specific about the problem** — give clear constraints and requirements
- **Avoid over-constraining** — let the model find its own reasoning path
- **Use structured output** — request JSON or specific formats for the final answer
- **Set appropriate think budgets** — balance quality vs. latency

| Resource | Type | Duration | Link |
|---|---|---|---|
| Prompting Reasoning Models — OpenAI Guide | 📖 Docs | ~15min | [Read](https://platform.openai.com/docs/guides/reasoning) |
| Prompt Engineering for Reasoning | 📖 Blog | ~20min | [Read](https://docs.anthropic.com/en/docs/build-with-claude/prompt-engineering/extended-thinking-tips) |

---

## ✅ Week 12 Checklist

- [ ] Understand how reasoning models differ from standard LLMs
- [ ] Know RLHF pipeline (SFT → Reward Model → PPO)
- [ ] Understand Chain of Thought and its variants
- [ ] Practice prompting reasoning models effectively
- [ ] Push your notes to `week-12/`

---

**⬅️ Previous: [Week 11: Evals — How to Avoid Hallucinations](../week-11/README.md)**
**➡️ Next: [Week 13: Image and Video Models](../week-13/README.md)**
