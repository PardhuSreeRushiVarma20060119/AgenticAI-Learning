# Agentic AI Engineering – n8n.io

## Day’s Goal
Experiment with building an **agentic AI workflow** inside **n8n** — focusing on tool usage, model orchestration, and conditional decision-making — inspired by concepts from my current *"Master AI Agents in 30 Days"* course.

**Intent:** Simulate the **core loop** of an AI agent:
```

Receive input → Analyze → Choose the right tool → Return a useful response

```
Do this in a **no-code/low-code** visual environment first.

---

## Setup Context
- **Platform:** [n8n.cloud]() (Trial account — 14 days, 1000 executions)
- **Framework type:** No-code / low-code
- **Key modules used:**
  - **Trigger:** "When chat message received"
  - **Processing Core:** AI Agent Node
  - **Model:** Google Gemini Chat Model
  - **Tool:** Calculator Node

This mirrors a small-scale **Agentic AI stack**:
- **AI Agent** → reasoning core
- **Tools** → “limbs”
- **Triggers** → “senses”

---

## Workflow Design

### **Step 1 – Entry Point**
**Trigger Node:** `When chat message received`  
**Purpose:** Listen for a user query in a chat interface.  
_Conceptually this acts as the event listener — the AI wakes up only when something comes in._

---

### **Step 2 – AI Agent Node**
- Functions as the **control brain**.
- Configured to:
  - Take the incoming message as input.
  - Decide whether to answer directly OR call a tool.
  - Retain minimal memory for context between tool calls.
- **Connected tools:** Calculator Node + Google Gemini Chat Model.

---

### **Step 3 – Google Gemini Chat Model**
- **Purpose:** Natural language understanding and reasoning.
- **Role:** Acts as the “primary thinking engine” when specialized tools aren’t required.
- Model integration: Gemini API key stored in n8n’s credentials manager.

---

### **Step 4 – Calculator Node**
- **Purpose:** Perform arithmetic operations.
- **Reasoning:** Even though LLMs *can* do math, explicit tool calls test “tool-augmented reasoning” rather than relying purely on LLM output.
- **Output format:** Boolean/numeric — caused formatting issues later.

---

## Execution Test

**Test Message Sent:**  
`2+2-4=?`

**Flow Execution Path:**
```

Trigger Node → AI Agent → Calculator Node → Return Response

```

**Observation:**
- AI correctly identified mathematical query → invoked Calculator.
- Calculator returned `0` as result.

---

## Reflections

### **Pros of n8n for Agentic Workflows**
- **Visual clarity:** Entire agent-tool chain visible at once.
- **Fast iteration:** No boilerplate — build rapidly.
- **Integration library:** Easy API, tool, and model connectors.

### **Cons / Limitations**
- **Limited advanced reasoning control:** Compared to code-first frameworks like LangGraph, CrewAI, or AutoGen.
- **Scaling complexity:** Multi-agent architectures become visually messy.

---

## Next Steps
1. **Add More Tools** — Web search, document lookup, database queries.
2. **Multi-Agent Chain** — e.g., Planner → Executor.
3. **Memory Upgrade** — Use vector DB in n8n for better context.
4. **Migrate to Code** — Rebuild in CrewAI or LangGraph for more fine-tuned control.

---

## Key Takeaways
- Even a basic n8n setup can demonstrate **core Agentic AI behavior**: sensing input, reasoning, choosing tools, returning answers.
- No-code tools are excellent for **prototypes** but hit flexibility limits.
- Early experiments are valuable for visualizing AI reasoning before moving to code-heavy implementations.

---

