# .NET AI Technology Decision Flow

> A choose-your-own-adventure guide to picking the right .NET AI technologies.

## START: What are you building?

```
 ┌─────────────────────────────────────────────────────┐
 │                  What are you building?              │
 └──────────────────────┬──────────────────────────────┘
                        │
      ┌─────────────────┼──────────────────────┐
      ▼                 ▼                      ▼
 ┌──────────┐   ┌──────────────┐       ┌──────────────┐
 │ AI in my │   │  AI Agents   │       │ Infra &      │
 │ app      │   │              │       │ Platform     │
 │ → STEP 1 │   │ → STEP 2     │       │ → STEP 3     │
 └──────────┘   └──────────────┘       └──────────────┘
```

---

## STEP 1 — Adding AI features to your app

*"I have an app and want to add AI capabilities"*

```
 What does the AI need to do?
 │
 ├─▶ Search my data with natural language
 │   └─▶ MEAI + MEVD ──── scenarios/semantic-search.md
 │
 ├─▶ Call APIs, look things up, take actions
 │   └─▶ MEAI (function calling) ──── scenarios/tool-calling.md
 │
 ├─▶ Have a conversation (multi-turn chat)
 │   │
 │   ├─ Need real-time streaming?
 │   │  └─▶ Yes ──── MEAI ──── scenarios/streaming-responses.md
 │   │
 │   └─ Full chat experience?
 │      └─▶ MEAI ──── scenarios/conversational-chat.md
 │
 ├─▶ Extract structured data from text
 │   └─▶ MEAI ──── scenarios/structured-data-extraction.md
 │
 ├─▶ Classify or categorize text
 │   └─▶ MEAI ──── scenarios/text-classification.md
 │
 ├─▶ Summarize documents
 │   └─▶ MEAI ──── scenarios/document-summarization.md
 │
 ├─▶ Generate images
 │   └─▶ MEAI ──── scenarios/image-generation.md
 │
 ├─▶ Filter content for safety/compliance
 │   └─▶ Azure AI Foundry + MEAI ──── scenarios/content-safety.md
 │
 └─▶ Just one simple AI call
     └─▶ MEAI ──── scenarios/single-ai-capability.md
```

---

## STEP 2 — Building AI Agents

*"I need agents that reason, plan, or coordinate"*

```
 How complex is the agent system?
 │
 ├─▶ Single agent with multi-step workflows
 │   └─▶ MAF + MEAI ──── scenarios/agent-orchestration.md
 │
 ├─▶ Multiple agents cooperating on tasks
 │   └─▶ MAF + MEAI ──── scenarios/multi-agent-coordination.md
 │
 ├─▶ Need a pre-built runtime (planning, code-aware, tools)
 │   └─▶ Copilot SDK + MEAI + MCP ──── scenarios/prebuilt-agent-runtime.md
 │
 ├─▶ Expose my tools/APIs so agents can use them
 │   └─▶ MCP ──── scenarios/expose-apis-to-ai.md
 │
 └─▶ Full production agent platform (enterprise-grade)
     └─▶ MAF + MEAI + MEVD + MCP + Azure AI Foundry + Aspire
         └──── scenarios/full-stack-agent-platform.md
```

---

## STEP 3 — Infrastructure & Platform

*"Where and how should my models run?"*

```
 Where does the model need to run?
 │
 ├─▶ ON MY MACHINE (local development)
 │   │
 │   │  What's your workflow?
 │   │
 │   ├─ Already using Docker?
 │   │  └─▶ Docker Model Runner + MEAI ──── scenarios/docker-local-inference.md
 │   │
 │   ├─ Need production parity with Azure?
 │   │  └─▶ Foundry Local + MEAI ──── scenarios/local-dev-foundry.md
 │   │
 │   └─ Just want free, easy, no API keys?
 │      └─▶ Ollama + MEAI ──── scenarios/local-dev-ollama.md
 │
 ├─▶ ON EDGE DEVICES (offline, low latency)
 │   └─▶ ONNX Runtime ──── scenarios/edge-device-inference.md
 │
 ├─▶ IN THE CLOUD (managed, scalable)
 │   └─▶ Azure AI Foundry ──── scenarios/managed-ai-infrastructure.md
 │
 └─▶ DISTRIBUTED SERVICES (orchestrate + observe)
     └─▶ Aspire ──── scenarios/service-orchestration.md
```

---

## Cross-Cutting Concerns

*Layer these on top of any path above:*

```
 ┌────────────────────────────────────────────────────────┐
 │  ✅ Content Safety    → Add Azure AI Foundry filters   │
 │  ✅ Observability     → Add Aspire                     │
 │  ✅ Tool Exposure     → Add MCP                        │
 │  ✅ Migrating from SK → See scenarios/migrate-from-     │
 │                          semantic-kernel.md             │
 └────────────────────────────────────────────────────────┘
```

---

## The Golden Rule

```
 MEAI is always the foundation.
 Start simple → add layers as you need them.

 Single call ──▶ + Tools ──▶ + Search ──▶ + Agents ──▶ + Platform
   (MEAI)      (MEAI+fn)   (+ MEVD)      (+ MAF)    (+ MCP+Aspire+Foundry)
```
