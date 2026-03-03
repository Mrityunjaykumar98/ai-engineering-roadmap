# Week 8: Advanced RAG and AI Safety

> **Goal:** Build a production-grade RAG application with advanced retrieval techniques and AI safety guardrails.

---

## 📋 Topics Covered

- **Reranking Strategies, Query Rewriting, HyDE**
- **Input and Output Guardrails**
- **AI Safety** — Prompt injection, Intent classification
- **🧪 Coding Assignment:** Build a RAG chatbot using API calls

---

## 🗺️ Learning Path

### Step 1: Advanced Retrieval Techniques

Basic RAG often retrieves the wrong chunks. Advanced techniques dramatically improve retrieval quality.

**Reranking:**
- After initial retrieval, use a cross-encoder to rerank results
- Cross-encoders are more accurate than bi-encoders but slower
- Retrieve 20-50 results, rerank, keep top 5

**Query Rewriting:**
- Rephrase user queries to improve retrieval
- "What's the refund policy?" → "refund policy cancellation return money"
- Use an LLM to generate multiple query variations

**HyDE (Hypothetical Document Embeddings):**
- Generate a hypothetical answer, then search for similar real documents
- Query: "How does photosynthesis work?" → LLM generates a draft answer → Embed the draft → Search for similar real documents

| Resource | Type | Duration | Link |
|---|---|---|---|
| Reranking for RAG — Cohere | 📖 Blog | ~20min | [Read](https://cohere.com/blog/reranking) |
| 7 Advanced RAG Techniques — LlamaIndex | 📖 Docs | ~30min | [Read](https://docs.llamaindex.ai/en/stable/optimizing/advanced_retrieval/query_transformations/) |
| HyDE Paper — Hypothetical Document Embeddings | 📄 Paper | ~30min | [Read](https://arxiv.org/abs/2212.10496) |
| Advanced RAG Techniques — DeepLearning.AI | 📹 Video | 1h | [Watch](https://www.youtube.com/watch?v=TRjq7t2Ms5I) |
| RAG From Scratch — LangChain (14-part series) | 📹 Video Series | ~3h | [Watch](https://www.youtube.com/playlist?list=PLfaIDFEXuae2LXbO1_PKyVJiQ23ZztA0x) |

---

### Step 2: Input & Output Guardrails

Production AI systems MUST have guardrails to prevent misuse and ensure safe outputs.

**Input guardrails:**
- **Content moderation:** Block toxic, harmful, or NSFW inputs
- **Intent classification:** Detect if the user is trying to jailbreak the model
- **Topic restriction:** Only allow queries about your domain
- **PII detection:** Block or redact personally identifiable information

**Output guardrails:**
- **Fact-checking against retrieved docs:** Only answer if the answer is in the context
- **Toxicity filtering:** Block harmful outputs
- **Format validation:** Ensure JSON/structured outputs are valid
- **Hallucination detection:** Flag outputs not grounded in source material

| Resource | Type | Duration | Link |
|---|---|---|---|
| Guardrails AI — Documentation | 📖 Docs | ~30min | [Read](https://www.guardrailsai.com/docs) |
| NeMo Guardrails — NVIDIA | 💻 Open Source | Reference | [GitHub](https://github.com/NVIDIA/NeMo-Guardrails) |
| LLM Guard — Input/Output Protection | 💻 Open Source | Reference | [GitHub](https://github.com/protectai/llm-guard) |
| Building Safe AI Systems — Anthropic | 📖 Article | ~20min | [Read](https://docs.anthropic.com/en/docs/about-claude/use-case-guides/content-moderation) |

---

### Step 3: AI Safety — Prompt Injection & Defense

Prompt injection is the #1 security vulnerability in LLM applications. An attacker crafts inputs that override the system prompt.

**Types of prompt injection:**
- **Direct injection:** "Ignore previous instructions and..."
- **Indirect injection:** Malicious instructions hidden in retrieved documents
- **Jailbreaking:** "Pretend you're DAN (Do Anything Now)"

**Defenses:**
- Input sanitization and pattern detection
- System prompt hardening
- Separate LLM calls for classification vs. generation
- Canary tokens in system prompts
- Instruction hierarchy (system > user > tool)

| Resource | Type | Duration | Link |
|---|---|---|---|
| Prompt Injection — Simon Willison | 📖 Blog | ~30min | [Read](https://simonwillison.net/2023/Apr/14/worst-that-can-happen/) |
| OWASP Top 10 for LLM Applications | 📖 Guide | ~1h | [Read](https://owasp.org/www-project-top-10-for-large-language-model-applications/) |
| Prompt Injection Defense Cheat Sheet | 📖 Resource | ~20min | [Read](https://llmsecurity.net/) |
| Not What You Signed Up For — Injection Paper | 📄 Paper | ~30min | [Read](https://arxiv.org/abs/2302.12173) |

---

## 🧪 Coding Assignment: Build a RAG Chatbot

Build a complete RAG chatbot that:

1. **Ingests documents** (PDF, web pages, or text files)
2. **Chunks and embeds** them into a vector database
3. **Accepts user queries** via a chat interface
4. **Retrieves relevant chunks** with reranking
5. **Generates answers** with source citations
6. **Includes guardrails** — input validation and output safety checks

**Tech stack suggestion:**
- LLM: Gemini API (free) or Groq (free)
- Embeddings: sentence-transformers
- Vector DB: ChromaDB
- Framework: LangChain
- UI: Streamlit
- Observability: LangSmith (free tier)

| Resource | Type | Link |
|---|---|---|
| LangChain RAG Tutorial | 📖 Tutorial | [Start](https://python.langchain.com/docs/tutorials/rag/) |
| Streamlit Chatbot Tutorial | 📖 Tutorial | [Start](https://docs.streamlit.io/develop/tutorials/llms/build-conversational-apps) |
| LangSmith — Free Tier | 📖 Docs | [Start](https://docs.smith.langchain.com/) |

---

## ✅ Week 8 Checklist

- [ ] Implement reranking in your RAG pipeline
- [ ] Understand HyDE and query rewriting
- [ ] Add input and output guardrails
- [ ] Understand prompt injection attacks and defenses
- [ ] Build a complete RAG chatbot with UI
- [ ] Push your chatbot code to `week-08/`

---

**⬅️ Previous: [Week 7: Retrieval Augmented Generation](../week-07/README.md)**
**➡️ Next: [Week 9: AI Agents and Tool Calling](../week-09/README.md)**
