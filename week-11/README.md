# Week 11: Evals — How to Avoid Hallucinations

> **Goal:** Learn how to build an evaluation framework, use LLM as a judge, and make tradeoffs between fine-tuning, prompting, and RAG.

---

## 📋 Topics Covered

- **LLM as a Judge**
- **Tradeoffs and Design Decisions**
- **Fine-tuning vs Prompting vs RAG**
- **🧪 Project:** Build your own LLM Judge

---

## 🗺️ Learning Path

### Step 1: Why Evals Matter

> "If you can't measure it, you can't improve it."

Evals are the **tests for AI applications**. Without them, you're shipping blind. Every change to prompts, models, or retrieval could silently break things.

**What to evaluate:**
- **Faithfulness:** Is the answer grounded in the provided context? (Not hallucinated)
- **Relevance:** Does the answer address the user's question?
- **Correctness:** Is the answer factually accurate?
- **Harmlessness:** Is the output safe and appropriate?
- **Coherence:** Is the response well-structured and readable?

| Resource | Type | Duration | Link |
|---|---|---|---|
| Your AI Product Needs Evals — Hamel Husain | 📖 Blog | ~30min | [Read](https://hamel.dev/blog/posts/evals/) |
| LLM Evaluation — DeepLearning.AI (Free) | 📚 Course | ~1h | [Start](https://www.deeplearning.ai/short-courses/building-evaluating-advanced-rag/) |
| Evaluating LLMs — Confident AI | 📖 Blog | ~20min | [Read](https://www.confident-ai.com/blog/llm-evaluation-metrics-everything-you-need-for-llm-evaluation) |
| Hallucination Leaderboard — Vectara | 📖 Resource | Reference | [Visit](https://huggingface.co/spaces/vectara/leaderboard) |

---

### Step 2: LLM as a Judge

Instead of human evaluation (expensive and slow), use another LLM to evaluate outputs. This is surprisingly effective and widely used in production.

**How it works:**
1. Define evaluation criteria in a prompt
2. Give the judge LLM the question, context, and answer
3. Ask it to score on a scale (1-5) with reasoning
4. Aggregate scores across your test set

**Considerations:**
- Use a stronger model as judge (GPT-4 judging GPT-3.5 outputs)
- Judges have biases (tend to prefer longer answers, their own outputs)
- Always validate judge quality against human ratings

| Resource | Type | Duration | Link |
|---|---|---|---|
| Judging LLM-as-a-Judge — LMSYS Paper | 📄 Paper | ~45min | [Read](https://arxiv.org/abs/2306.05685) |
| LLM Judge Patterns — Hamel Husain | 📖 Blog | ~20min | [Read](https://hamel.dev/blog/posts/llm-judge/) |
| DeepEval — LLM Evaluation Framework | 📖 Docs | ~30min | [Start](https://docs.confident-ai.com/) |
| OpenAI Evals Framework | 💻 Open Source | Reference | [GitHub](https://github.com/openai/evals) |
| RAGAS — RAG Evaluation | 💻 Open Source | Reference | [GitHub](https://github.com/explodinggradients/ragas) |

---

### Step 3: Fine-tuning vs Prompting vs RAG

One of the most important decisions in AI engineering. There's no single right answer — it depends on your use case.

| Approach | Best For | Cost | Latency | Updatability |
|---|---|---|---|---|
| **Prompting** | Simple tasks, quick iteration | Low | Fast | Easy (change prompt) |
| **RAG** | Knowledge-intensive, frequently updated data | Medium | Medium | Easy (update docs) |
| **Fine-tuning** | Consistent style/format, domain expertise | High | Fast (at inference) | Hard (retrain) |

**Rules of thumb:**
1. Start with prompting — it's free and fast
2. If prompting isn't enough, add RAG
3. Only fine-tune when prompting + RAG can't solve your problem
4. Often the best solution combines all three

| Resource | Type | Duration | Link |
|---|---|---|---|
| When to Fine-tune vs RAG vs Prompt — Chip Huyen | 📖 Blog | ~30min | [Read](https://huyenchip.com/2023/04/11/llm-engineering.html) |
| Fine-tuning vs RAG — Anyscale | 📖 Blog | ~20min | [Read](https://www.anyscale.com/blog/fine-tuning-vs-rag) |
| Prompt Engineering Guide — Anthropic | 📖 Guide | ~1h | [Read](https://docs.anthropic.com/en/docs/build-with-claude/prompt-engineering/overview) |
| Learn Prompting (Full Free Course) | 📚 Course | Self-paced | [Start](https://learnprompting.org/) |

---

## 🧪 Project: Build Your Own LLM Judge

Build an evaluation pipeline that:

1. **Create a test dataset** — 20-50 question-answer pairs with ground truth
2. **Implement evaluation metrics:**
   - Faithfulness (is the answer grounded in context?)
   - Relevance (does it answer the question?)
   - Correctness (is it factually accurate?)
3. **Build an LLM Judge** that scores outputs on each metric
4. **Compare results** of your RAG chatbot (from Week 8) on these metrics
5. **Iterate** — improve prompts/retrieval based on eval results

---

## ✅ Week 11 Checklist

- [ ] Understand why evals are essential for production AI
- [ ] Know the key evaluation metrics for LLM apps
- [ ] Implement LLM-as-a-Judge scoring
- [ ] Understand when to use prompting vs RAG vs fine-tuning
- [ ] Build your LLM Judge project
- [ ] Push your eval code to `week-11/`

---

**⬅️ Previous: [Week 10: MCP, Context Engineering, Multi-Agent Systems](../week-10/README.md)**
**➡️ Next: [Week 12: Reasoning Models](../week-12/README.md)**
