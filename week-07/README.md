# Week 7: Retrieval Augmented Generation (RAG)

> **Goal:** Learn chunking strategies, data ingestion, reranking, indexing, vector databases, and other techniques for RAG.

> 🔴 **Full Stack Dev: THIS IS YOUR #1 SKILL.** RAG is how you add AI to 90% of real products — search over docs, customer support, knowledge bases, internal tools. You already know databases; vector databases are just databases optimized for similarity search. LangChain/LlamaIndex are your Express.js/Django equivalents for AI.



## 📋 Topics Covered

- **RAG pipeline** — Chunking strategies, data ingestion, reranker, indexer
- **Vector Embeddings & Vector Databases**
- **Search Algorithms** — ANN algorithms (HNSW, IVF)

---

## 🗺️ Learning Path

### Step 1: What is RAG and Why Do We Need It?

LLMs have a knowledge cutoff and can hallucinate facts. RAG solves this by **retrieving relevant documents** from a knowledge base and feeding them to the LLM as context.

```
User Query → Search Knowledge Base → Retrieve Top Documents → LLM(Query + Documents) → Answer
```

**Why RAG over fine-tuning?**
- No training required — just add documents
- Easy to update (add/remove docs)
- Source attribution — you know WHERE the answer came from
- Cheaper and faster than fine-tuning

| Resource | Type | Duration | Link |
|---|---|---|---|
| What is RAG? — IBM | 📹 Video | 10min | [Watch](https://www.youtube.com/watch?v=T-D1OfcDW1M) |
| RAG Paper (Original) | 📄 Paper | ~45min | [Read](https://arxiv.org/abs/2005.11401) |
| LangChain RAG Conceptual Guide | 📖 Docs | ~20min | [Read](https://python.langchain.com/docs/concepts/rag/) |
| Full Stack RAG — Weights & Biases (Free Course) | 📚 Course | ~3h | [Start](https://www.wandb.courses/courses/rag-in-production) |

---

### Step 2: Chunking Strategies

Before documents can be searched, they need to be split into chunks. The chunking strategy dramatically affects RAG quality.

**Common strategies:**
- **Fixed-size chunking:** Split every N characters/tokens (simple, can break sentences)
- **Sentence-based chunking:** Split on sentence boundaries
- **Recursive character splitting:** LangChain's default — split on paragraphs, then sentences, then characters
- **Semantic chunking:** Use embeddings to find natural breakpoints
- **Document-aware chunking:** Respect headers, sections, tables

**Key parameters:**
- **Chunk size:** Typically 256–1024 tokens
- **Chunk overlap:** 10-20% overlap to preserve context across boundaries

| Resource | Type | Duration | Link |
|---|---|---|---|
| Chunking Strategies for RAG — Pinecone | 📖 Article | ~20min | [Read](https://www.pinecone.io/learn/chunking-strategies/) |
| 5 Levels of Chunking — Greg Kamradt | 📹 Video | 30min | [Watch](https://www.youtube.com/watch?v=8OJC21T2SL4) |
| Chunking Strategies — LlamaIndex | 📖 Docs | ~15min | [Read](https://docs.llamaindex.ai/en/stable/module_guides/loading/node_parsers/) |

---

### Step 3: Vector Embeddings & Vector Databases

After chunking, each chunk is converted to a vector embedding and stored in a vector database for fast similarity search.

**Popular embedding models (free):**
- `sentence-transformers/all-MiniLM-L6-v2` — Fast, good quality
- `BAAI/bge-small-en-v1.5` — Best quality/size ratio
- `nomic-embed-text-v1.5` — Open source, great quality
- Google Gemini Embedding API (free tier)

**Popular vector databases:**
- **ChromaDB:** Dead simple, great for learning (runs in-memory or persistent)
- **FAISS:** Facebook's library, fastest for local use
- **Qdrant:** Production-ready, open source
- **Pinecone:** Managed service (free tier available)

| Resource | Type | Duration | Link |
|---|---|---|---|
| ChromaDB — Getting Started | 📖 Docs | ~30min | [Start](https://docs.trychroma.com/getting-started) |
| FAISS Tutorial — Facebook Research | 💻 Code | ~30min | [Start](https://github.com/facebookresearch/faiss/wiki/Getting-started) |
| Vector Database Explained — James Briggs | 📹 Video | 20min | [Watch](https://www.youtube.com/watch?v=dN0lsF2cvm4) |
| Sentence Transformers Guide | 📖 Docs | ~20min | [Read](https://www.sbert.net/docs/quickstart.html) |
| MTEB Embedding Leaderboard | 📖 Resource | Reference | [Visit](https://huggingface.co/spaces/mteb/leaderboard) |

---

### Step 4: Search Algorithms — HNSW & IVF

Finding the nearest vectors in millions of documents requires specialized algorithms.

**Approximate Nearest Neighbor (ANN) algorithms:**
- **HNSW (Hierarchical Navigable Small Worlds):** Graph-based, great recall, used by most vector DBs
- **IVF (Inverted File Index):** Clusters vectors, searches within clusters
- **Flat (Brute Force):** Exact search — accurate but slow for large datasets

| Resource | Type | Duration | Link |
|---|---|---|---|
| HNSW Explained — Pinecone | 📖 Article | ~20min | [Read](https://www.pinecone.io/learn/series/faiss/hnsw/) |
| Vector Search Algorithms | 📹 Video | 25min | [Watch](https://www.youtube.com/watch?v=QvKMwLjdK-s) |
| FAISS Guide by Pinecone (comprehensive) | 📖 Article | ~30min | [Read](https://www.pinecone.io/learn/series/faiss/) |

> **📄 Research Paper:** [Efficient and Robust Approximate Nearest Neighbor Search (HNSW) — Malkov & Yashunin, 2018](https://arxiv.org/abs/1603.09320)

---

## 🧪 Practice Exercise

### Build a basic RAG pipeline:

1. Load a set of PDF/text documents
2. Chunk them using recursive character splitting
3. Generate embeddings using sentence-transformers
4. Store in ChromaDB
5. Query the system with natural language questions
6. Retrieve top-k relevant chunks and display them

Use [LangChain's RAG Tutorial](https://python.langchain.com/docs/tutorials/rag/) as a guide.

---

## ✅ Week 7 Checklist

- [ ] Understand why RAG is needed and when to use it vs. fine-tuning
- [ ] Know the different chunking strategies and their tradeoffs
- [ ] Set up ChromaDB locally and store/query embeddings
- [ ] Understand HNSW at a high level
- [ ] Build a basic RAG pipeline
- [ ] Push your RAG code to `week-07/`

---

**⬅️ Previous: [Week 6: Quantization and Fine-Tuning](../week-06/README.md)**
**➡️ Next: [Week 8: Advanced RAG and AI Safety](../week-08/README.md)**
