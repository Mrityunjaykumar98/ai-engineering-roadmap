# Week 15: Capstone Project

> **Goal:** Build a complete AI application from scratch, combining everything you've learned.

---

## 📋 Objectives

- Choose an industry-relevant idea
- Apply learnings from Weeks 1–14
- Build, test, and document your project
- Present and showcase your work

---

## 🗺️ Project Guidelines

### Step 1: Choose Your Project

Pick a project that demonstrates at least **3-4 major concepts** from the course. Here are some ideas:

#### 🔥 Project Ideas

| Project | Concepts Used | Difficulty |
|---|---|---|
| **AI Research Assistant** | RAG + Agents + Evals + Web UI | ⭐⭐⭐ |
| **Customer Support Chatbot** | RAG + Tool Calling + Guardrails + Memory | ⭐⭐ |
| **Code Review Agent** | Multi-Agent + Tool Calling + Evals | ⭐⭐⭐ |
| **Document Q&A with Citations** | RAG + Reranking + Streamlit UI | ⭐⭐ |
| **AI Tutor** | RAG + Memory + CoT + Evals | ⭐⭐⭐ |
| **Content Generation Pipeline** | Fine-tuning + Diffusion + Agents | ⭐⭐⭐⭐ |
| **Multi-Agent Debate System** | Multi-Agent + Reasoning + Evals | ⭐⭐⭐ |
| **AI-Powered Search Engine** | RAG + Embeddings + Vector DB + Web Crawling | ⭐⭐⭐ |

---

### Step 2: Build It

**Recommended architecture:**

```
User Interface (Streamlit / Next.js)
        ↓
Application Layer (LangChain / LangGraph)
        ↓
┌─────────────┬──────────────┬─────────────┐
│  LLM API    │  Vector DB   │  Tools/MCP   │
│  (Gemini)   │  (ChromaDB)  │  (Custom)    │
└─────────────┴──────────────┴─────────────┘
        ↓
Observability (LangSmith / Phoenix)
        ↓
Evaluation (DeepEval / Custom Evals)
```

**Submission requirements:**
1. Working application with a clean UI
2. README with architecture diagram and setup instructions
3. Evaluation results showing your system's quality metrics
4. At least 3 tools/integrations
5. Guard rails and safety measures

---

### Step 3: Evaluate Your Project

Use the evaluation techniques from Week 11:
- Define at least 5 evaluation criteria
- Create a test dataset (20+ examples)
- Run your LLM Judge against your system
- Report scores and identify areas for improvement

---

### Step 4: Document & Showcase

**Your README should include:**
- Problem statement and motivation
- Architecture overview (with diagram)
- Tech stack and setup instructions
- Demo screenshots/video
- Evaluation results
- Known limitations and future improvements

---

## 📚 Useful Templates & Resources

| Resource | Type | Link |
|---|---|---|
| LangChain Templates | 💻 Starter Code | [GitHub](https://github.com/langchain-ai/langchain/tree/master/templates) |
| Streamlit App Gallery | 🎨 Inspiration | [Visit](https://streamlit.io/gallery) |
| Vercel AI SDK Templates | 💻 Templates | [Visit](https://sdk.vercel.ai/docs/introduction) |
| AI Project README Template | 📖 Template | [GitHub](https://github.com/matiassingers/awesome-readme) |

---

## ✅ Week 15 Checklist

- [ ] Choose and scope your project idea
- [ ] Set up the project repository and architecture
- [ ] Implement core functionality
- [ ] Add evaluation pipeline
- [ ] Build UI and polish
- [ ] Write documentation and README
- [ ] Push everything to `week-15/`

---

**⬅️ Previous: [Week 14: Diffusion Based Models](../week-14/README.md)**
**➡️ Next: [Week 16: AI Engineering Principles](../week-16/README.md)**
