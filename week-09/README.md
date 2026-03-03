# Week 9: AI Agents and Tool Calling

> **Goal:** Learn what an Agent is, how they are different from plain LLMs, Tool Calling, ReAct pattern, and Agent Orchestration.

---

## 📋 Topics Covered

- **LLM vs Agent vs Multiple Agents**
- **ReAct Pattern** — Reasoning + Acting
- **Prompt Chaining, Orchestration, Routing**
- **🧪 Coding Assignment:** Build a customer support agent

---

## 🗺️ Learning Path

### Step 1: LLMs vs Agents

A plain LLM just generates text. An **Agent** is an LLM that can:
1. **Observe** — Read the current state/context
2. **Think** — Reason about what to do next
3. **Act** — Use tools (search, code, APIs, databases)
4. **Repeat** — Continue until the task is complete

```
User: "What's the weather in Mumbai and should I carry an umbrella?"

LLM: "I don't have real-time weather data..."

Agent:
  Think: I need current weather data → I should use the weather API
  Act: call weather_api("Mumbai") → 28°C, 80% rain chance
  Think: High rain probability → recommend umbrella
  Respond: "Currently 28°C in Mumbai with 80% chance of rain. Yes, carry an umbrella!"
```

| Resource | Type | Duration | Link |
|---|---|---|---|
| LLM Powered Autonomous Agents — Lilian Weng | 📖 Blog | ~1h | [Read](https://lilianweng.github.io/posts/2023-06-23-agent/) |
| What are AI Agents? — Andrew Ng | 📹 Video | 15min | [Watch](https://www.youtube.com/watch?v=sal78ACtGTc) |
| Building Effective Agents — Anthropic | 📖 Blog | ~30min | [Read](https://docs.anthropic.com/en/docs/build-with-claude/agent-patterns) |
| AI Agents in Production — DeepLearning.AI | 📚 Course | ~3h | [Start](https://www.deeplearning.ai/short-courses/ai-agents-in-langgraph/) |

---

### Step 2: Tool Calling / Function Calling

Tool calling lets the LLM invoke external functions. The model doesn't actually execute the function — it outputs a structured request, and your code executes it.

```json
Model output:
{
  "function": "search_database",
  "arguments": {"query": "return policy", "limit": 5}
}

→ Your code calls search_database("return policy", 5)
→ Results fed back to the model
→ Model generates final answer using results
```

| Resource | Type | Duration | Link |
|---|---|---|---|
| OpenAI Function Calling Guide | 📖 Docs | ~20min | [Read](https://platform.openai.com/docs/guides/function-calling) |
| Gemini Function Calling | 📖 Docs | ~20min | [Read](https://ai.google.dev/gemini-api/docs/function-calling) |
| LangChain — Tool Use | 📖 Docs | ~30min | [Read](https://python.langchain.com/docs/concepts/tool_calling/) |
| Build a Tool-using Agent from Scratch | 📹 Video | 40min | [Watch](https://www.youtube.com/watch?v=aqdWSYWC_LI) |

---

### Step 3: The ReAct Pattern

**ReAct = Reasoning + Acting.** The agent explicitly outputs its reasoning before acting.

```
Question: What is the population of the capital of France?

Thought 1: I need to find the capital of France.
Action 1: search("capital of France")
Observation 1: Paris is the capital of France.

Thought 2: Now I need the population of Paris.
Action 2: search("population of Paris")
Observation 2: The population of Paris is ~2.1 million.

Thought 3: I have the answer.
Answer: The population of the capital of France (Paris) is approximately 2.1 million.
```

| Resource | Type | Duration | Link |
|---|---|---|---|
| ReAct Paper | 📄 Paper | ~45min | [Read](https://arxiv.org/abs/2210.03629) |
| ReAct Explained — Yannic Kilcher | 📹 Video | 30min | [Watch](https://www.youtube.com/watch?v=Eug2clsLtFs) |
| Build a ReAct Agent — LangChain | 📖 Tutorial | ~30min | [Read](https://python.langchain.com/docs/tutorials/agents/) |

---

### Step 4: Agent Orchestration & Routing

For complex tasks, you need to **orchestrate multiple steps** — routing queries to different tools, chaining outputs, and handling errors.

**Patterns:**
- **Prompt Chaining:** Output of step 1 → input of step 2
- **Routing:** Classify the query, then route to the right handler
- **Parallel tool calls:** Run multiple tools simultaneously
- **Fallback chains:** If tool A fails, try tool B

| Resource | Type | Duration | Link |
|---|---|---|---|
| LangGraph — Agent Orchestration | 📖 Docs + Tutorial | ~1h | [Start](https://langchain-ai.github.io/langgraph/) |
| Agent Architecture Patterns — LangChain | 📖 Blog | ~20min | [Read](https://blog.langchain.dev/planning-agents/) |
| CrewAI — Multi-Agent Framework | 📖 Docs | Reference | [Start](https://docs.crewai.com/) |

---

## 🧪 Coding Assignment: Customer Support Agent

Build an AI agent that handles customer support:

1. **Tools:** Search product catalog, lookup order status, check return policy
2. **Pattern:** ReAct with tool calling
3. **Features:** Multi-turn conversation, graceful error handling
4. **Bonus:** Route to human agent for complex issues

---

## ✅ Week 9 Checklist

- [ ] Understand the difference between LLMs and Agents
- [ ] Implement tool calling with at least 3 tools
- [ ] Build a ReAct agent
- [ ] Understand orchestration patterns
- [ ] Complete the customer support agent assignment
- [ ] Push your agent code to `week-09/`

---

**⬅️ Previous: [Week 8: Advanced RAG and AI Safety](../week-08/README.md)**
**➡️ Next: [Week 10: MCP, Context Engineering, Multi-Agent Systems](../week-10/README.md)**
