# Week 10: MCP, Context Engineering, Multi-Agent Systems

> **Goal:** Code an AI Agent with MCP and memory, optimizing agentic flow.

---

## 📋 Topics Covered

- **Context Engineering** — Managing what the model "knows"
- **Memory in Agents** — Short-term, long-term, episodic
- **MCP (Model Context Protocol) & A2A**
- **Multi-Agent Systems**
- **🧪 Coding Assignment:** MCP with memory and optimizing agentic flow

---

## 🗺️ Learning Path

### Step 1: Context Engineering

Context engineering is the art of controlling **what information** goes into the model's context window. It's broader than prompt engineering — it includes retrieval, memory, tool outputs, and dynamic context selection.

**Key principles:**
- Every token in the context window is valuable real estate
- Prioritize relevant information over complete information
- Summarize older conversation turns to save space
- Dynamically inject context based on the current query

| Resource | Type | Duration | Link |
|---|---|---|---|
| Context Engineering — Simon Willison | 📖 Blog | ~30min | [Read](https://simonwillison.net/2025/Jun/27/context-engineering/) |
| Building Effective Agents — Anthropic | 📖 Blog | ~30min | [Read](https://docs.anthropic.com/en/docs/build-with-claude/agent-patterns) |
| Long Context vs. RAG | 📖 Blog | ~20min | [Read](https://blog.langchain.dev/long-context-rag/) |

---

### Step 2: Memory in Agents

Agents need memory to maintain context across conversations and learn from experience.

**Types of memory:**
- **Short-term (Working) Memory:** Current conversation context
- **Long-term Memory:** Persistent facts stored across sessions (user preferences, past interactions)
- **Episodic Memory:** Memories of specific past events/conversations
- **Semantic Memory:** General knowledge and facts

**Implementation approaches:**
- In-context memory (stuff recent messages in the prompt)
- Summary memory (LLM summarizes older messages)
- Vector store memory (embed and retrieve relevant past conversations)
- Structured memory (key-value store for user facts)

| Resource | Type | Duration | Link |
|---|---|---|---|
| Memory in AI Agents — LangChain | 📖 Docs | ~30min | [Read](https://python.langchain.com/docs/concepts/memory/) |
| Mem0 — Memory Layer for AI | 💻 Open Source | Reference | [GitHub](https://github.com/mem0ai/mem0) |
| MemGPT Paper — Virtual Context Management | 📄 Paper | ~30min | [Read](https://arxiv.org/abs/2310.08560) |

---

### Step 3: Model Context Protocol (MCP) & A2A

**MCP** is an open protocol (by Anthropic) that standardizes how AI models connect to external data sources and tools. Think of it as the "USB-C for AI" — a universal plug-and-play standard.

**A2A (Agent-to-Agent)** is Google's protocol for agents to communicate with each other.

**Why MCP matters:**
- Standardized tool interface — one protocol, many tools
- Tools can be developed independently and shared
- Reduces custom integration code

| Resource | Type | Duration | Link |
|---|---|---|---|
| MCP Documentation — Anthropic | 📖 Docs | ~1h | [Read](https://modelcontextprotocol.io/) |
| MCP Quickstart Guide | 📖 Tutorial | ~30min | [Start](https://modelcontextprotocol.io/quickstart) |
| MCP Servers Repository | 💻 Open Source | Reference | [GitHub](https://github.com/modelcontextprotocol/servers) |
| A2A Protocol — Google | 📖 Docs | ~30min | [Read](https://google.github.io/A2A/) |
| Build an MCP Server — Practical Tutorial | 📹 Video | 30min | [Watch](https://www.youtube.com/watch?v=kQmXtrmQ5Zg) |

---

### Step 4: Multi-Agent Systems

Instead of one agent doing everything, **multiple specialized agents collaborate** on complex tasks.

**Architectures:**
- **Supervisor:** One manager agent delegates to worker agents
- **Swarm:** Agents pass control between themselves
- **Hierarchical:** Nested teams with sub-managers
- **Debate:** Agents argue to reach better conclusions

| Resource | Type | Duration | Link |
|---|---|---|---|
| Multi-Agent Systems — LangGraph | 📖 Docs | ~30min | [Read](https://langchain-ai.github.io/langgraph/concepts/multi_agent/) |
| AutoGen — Microsoft Multi-Agent | 💻 Open Source | Reference | [GitHub](https://microsoft.github.io/autogen/) |
| CrewAI — Build Agent Teams | 📖 Docs | ~30min | [Start](https://docs.crewai.com/) |
| Multi-Agent Debate Paper | 📄 Paper | ~30min | [Read](https://arxiv.org/abs/2305.19118) |

---

## 🧪 Coding Assignment

Build an AI agent system with:
1. **MCP integration** — Connect to at least 2 external tools via MCP
2. **Memory** — Persistent memory across conversations
3. **Multi-agent** — At least 2 specialized agents collaborating

---

## ✅ Week 10 Checklist

- [ ] Understand context engineering principles
- [ ] Implement agent memory (short-term and long-term)
- [ ] Set up an MCP server and connect to it
- [ ] Build a multi-agent system
- [ ] Push your code to `week-10/`

---

**⬅️ Previous: [Week 9: AI Agents and Tool Calling](../week-09/README.md)**
**➡️ Next: [Week 11: Evals — How to Avoid Hallucinations](../week-11/README.md)**
