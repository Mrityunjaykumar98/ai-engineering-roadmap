# Week 16: AI Engineering Principles

> **Goal:** Recap your learnings and master best practices for building production AI systems.

---

## 📋 Topics Covered

- **Short Recap** of the entire program
- **Best Practices** when working with LLMs
- **Limitations of GenAI** at work
- **Transitioning to AI Engineering**

---

## 🗺️ Learning Path

### Step 1: Program Recap

```
Weeks 1-3:   FOUNDATIONS        Neural Networks → Tokenization → Attention
Weeks 4-6:   INTERNALS          Transformers → Training → Quantization + Fine-tuning
Weeks 7-8:   RETRIEVAL          RAG → Advanced RAG + Safety
Weeks 9-10:  AGENTS             Tool Calling → MCP + Multi-Agents
Weeks 11-12: PRODUCTION         Evals → Reasoning Models
Weeks 13-14: MULTIMODAL         Image/Video Models → Diffusion
Weeks 15-16: CAPSTONE           Build + Ship + Best Practices
```

**You can now explain and implement:**
- ✅ How transformers work from first principles
- ✅ How LLMs are trained, fine-tuned, and quantized
- ✅ RAG systems with advanced retrieval and safety
- ✅ AI agents with tool calling, memory, and MCP
- ✅ Evaluation frameworks and LLM-as-Judge
- ✅ Image and video generation with diffusion models

---

### Step 2: Best Practices for Production LLMs

**Prompt Engineering:**
- Version control your prompts
- Test prompts against evaluation sets before deploying
- Use system prompts for consistent behavior
- Include few-shot examples for complex tasks

**Architecture:**
- Start simple — don't over-engineer
- Use RAG before fine-tuning
- Cache responses for common queries
- Implement rate limiting and cost tracking

**Reliability:**
- Always have fallback strategies
- Implement retry logic with exponential backoff
- Monitor latency, cost, and quality metrics
- Use structured outputs (JSON mode) when possible

**Safety:**
- Never trust user input directly
- Implement input/output guardrails
- Log everything for debugging and auditing
- Have a human-in-the-loop for critical decisions

| Resource | Type | Duration | Link |
|---|---|---|---|
| Building LLM Applications — Chip Huyen | 📖 Blog | ~1h | [Read](https://huyenchip.com/2023/04/11/llm-engineering.html) |
| Patterns for Building LLM Apps — a16z | 📖 Blog | ~30min | [Read](https://a16z.com/emerging-architectures-for-llm-applications/) |
| Anthropic's Prompt Engineering Guide | 📖 Guide | ~1h | [Read](https://docs.anthropic.com/en/docs/build-with-claude/prompt-engineering/overview) |
| Google's MlOps Best Practices | 📖 Docs | ~30min | [Read](https://cloud.google.com/architecture/mlops-continuous-delivery-and-automation-pipelines-in-machine-learning) |
| Building Effective Agents — Anthropic | 📖 Blog | ~30min | [Read](https://docs.anthropic.com/en/docs/build-with-claude/agent-patterns) |

---

### Step 3: Limitations of GenAI

Understanding what AI **can't** do is as important as knowing what it can.

**Current limitations:**
- **Hallucinations:** Models confidently state false information
- **Reasoning:** Still struggles with novel multi-step logic
- **Consistency:** Same prompt can give different results
- **Knowledge cutoff:** Models don't know recent events
- **Math/Counting:** Unreliable for precise calculations
- **Privacy:** Models can leak training data
- **Bias:** Models reflect biases in training data
- **Cost:** High-quality AI at scale is expensive

| Resource | Type | Duration | Link |
|---|---|---|---|
| AI Snake Oil (Book) — Arvind Narayanan | 📖 Book | ~1h excerpts | [Read](https://www.aisnakeoil.com/) |
| Limitations of LLMs — Yann LeCun | 📹 Video | 30min | [Watch](https://www.youtube.com/watch?v=mIbftNqOoJg) |
| Sparks of AGI — Microsoft Paper (GPT-4) | 📄 Paper | ~1h | [Read](https://arxiv.org/abs/2303.12712) |

---

### Step 4: Transitioning to AI Engineering

**AI Engineering skills that are essential:**
1. **System Design** for AI applications
2. **Evaluation-driven development** (evals → build → evaluate → iterate)
3. **Cost optimization** (model selection, caching, batching)
4. **Choosing the right model** for each use case
5. **Understanding tradeoffs** (latency vs quality vs cost)

**Career resources:**

| Resource | Type | Link |
|---|---|---|
| AI Engineer Roadmap — latent.space | 📖 Blog | [Read](https://www.latent.space/p/2024-ai-engineer) |
| LLM Engineers Handbook | 📖 Book (Free chapters) | [GitHub](https://github.com/PacktPublishing/LLM-Engineers-Handbook) |
| Awesome LLM Resources | 💻 Curated List | [GitHub](https://github.com/Hannibal046/Awesome-LLM) |

---

### 🎓 Essential Reading List (must read research papers)

| # | Paper | Year | Topic |
|---|---|---|---|
| 1 | [Attention Is All You Need](https://arxiv.org/abs/1706.03762) | 2017 | Transformers |
| 2 | [BERT](https://arxiv.org/abs/1810.04805) | 2018 | Bidirectional Pre-training |
| 3 | [GPT-2](https://cdn.openai.com/better-language-models/language_models_are_unsupervised_multitask_learners.pdf) | 2019 | Language Models |
| 4 | [Scaling Laws for Neural LMs](https://arxiv.org/abs/2001.08361) | 2020 | Scaling |
| 5 | [DDPM](https://arxiv.org/abs/2006.11239) | 2020 | Diffusion Models |
| 6 | [CLIP](https://arxiv.org/abs/2103.00020) | 2021 | Vision-Language |
| 7 | [LoRA](https://arxiv.org/abs/2106.09685) | 2021 | Efficient Fine-tuning |
| 8 | [InstructGPT (RLHF)](https://arxiv.org/abs/2203.02155) | 2022 | Alignment |
| 9 | [Chain of Thought](https://arxiv.org/abs/2201.11903) | 2022 | Reasoning |
| 10 | [Flash Attention](https://arxiv.org/abs/2205.14135) | 2022 | Efficient Attention |
| 11 | [RAG](https://arxiv.org/abs/2005.11401) | 2022 | Retrieval |
| 12 | [Latent Diffusion (Stable Diffusion)](https://arxiv.org/abs/2112.10752) | 2022 | Image Generation |
| 13 | [QLoRA](https://arxiv.org/abs/2305.14314) | 2023 | Efficient Fine-tuning |
| 14 | [ReAct](https://arxiv.org/abs/2210.03629) | 2023 | Agents |
| 15 | [DPO](https://arxiv.org/abs/2305.18290) | 2023 | Alignment |
| 16 | [DeepSeek R1](https://arxiv.org/abs/2501.12948) | 2025 | Reasoning Models |

---

## ✅ Week 16 Checklist

- [ ] Complete and polish your capstone project
- [ ] Review the best practices for production LLMs
- [ ] Understand the limitations of current AI
- [ ] Read at least 5 papers from the essential reading list
- [ ] Update your resume with AI Engineering skills
- [ ] Push final notes and reflections to `week-16/`

---

## 🎉 Congratulations!

You've completed the AI Engineering Roadmap. You now have the knowledge and hands-on experience to:
- **Build** production-grade AI applications
- **Understand** LLMs from first principles
- **Evaluate** and improve AI systems
- **Make informed** technical decisions about AI

**Keep building. Keep learning. The field moves fast, and so should you. 🚀**

---

**⬅️ Previous: [Week 15: Capstone Project](../week-15/README.md)**
**🏠 Home: [AI Engineering Roadmap](../README.md)**
