# Examples

> Auto-generated from scenario files. Do not edit directly.

Real-world examples of .NET AI scenarios, grouped by category.

## Agent Orchestration

### [Agent Orchestration](scenarios/agent-orchestration.md) ([repo](https://github.com/microsoft/agent-framework/tree/main/dotnet/samples/))

An insurance claims agent that triages submissions, routes to specialist agents (auto, property, health), and produces recommendations with full reasoning chains.

### [Multi-Agent Coordination](scenarios/multi-agent-coordination.md) ([repo](https://github.com/microsoft/agent-framework/tree/main/dotnet/samples/))

An enterprise HR platform where a supervisor agent routes employee requests to specialized sub-agents: one handles benefits questions (with access to benefits APIs), another handles PTO requests (with calendar and approval tools), and a third handles IT provisioning (with Active Directory and ticketing tools). The supervisor manages handoffs and ensures each request reaches the right specialist.

## Cloud-Native Operations

### [Full-Stack Agent Platform](scenarios/full-stack-agent-platform.md) ([repo](https://github.com/dotnet/aspire-samples))

An insurance company building a claims processing platform. A supervisor agent triages incoming claims and routes to specialist agents (auto, property, health). Each specialist has access to domain-specific tools (policy lookup, damage assessment APIs) and a knowledge base of claim guidelines. MCP servers expose the platform's capabilities to other internal AI assistants. Aspire orchestrates all services and provides end-to-end distributed tracing from user submission through agent reasoning to claim resolution.

### [Service Orchestration and Observability](scenarios/service-orchestration.md) ([repo](https://github.com/dotnet/aspire-samples))

A multi-service support agent where Aspire ensures the API, agent, vector store, and model endpoint are all running, connected, and observable. Distributed tracing shows end-to-end request flow from user question through agent reasoning to model call and back.

## Content Generation

### [Image Generation](scenarios/image-generation.md) ([repo](https://github.com/dotnet/ai-samples/tree/main/src/microsoft-extensions-ai/))

A content management system that generates social media images from article summaries. Content editors enter a description, and the system produces branded visuals ready for publishing.

## Content Safety

### [Content Safety and Moderation](scenarios/content-safety.md) ([repo](https://github.com/dotnet/ai-samples/tree/main/src/microsoft-extensions-ai/))

A healthcare company deploying a patient-facing chatbot. Foundry's content filters block harmful medical advice and PII exposure at the platform layer. A custom MEAI middleware component additionally checks responses against an approved medical knowledge base to prevent hallucinated treatment recommendations.

## Core AI Integration

### [Conversational Chat Interface](scenarios/conversational-chat.md) ([repo](https://github.com/dotnet/ai-samples/tree/main/src/microsoft-extensions-ai/))

A SaaS platform adding an AI assistant sidebar to its dashboard. Users ask questions about their data, and the assistant maintains context across turns — remembering what was discussed, referring back to earlier questions, and refining its answers as the conversation progresses. A system prompt defines the assistant's persona and access boundaries.

### [Document Summarization](scenarios/document-summarization.md) ([repo](https://github.com/dotnet/ai-samples/tree/main/src/microsoft-extensions-ai/))

A law firm's document management system that automatically generates executive summaries of incoming briefs and filings. Attorneys see a one-paragraph summary and key points before deciding whether to read the full document. The system caches summaries so repeated access is instant.

### [Add a Single AI Capability](scenarios/single-ai-capability.md) ([repo](https://github.com/dotnet/ai-samples/tree/main/src/microsoft-extensions-ai/))

An e-commerce app that generates product descriptions from catalog data. The product team enters raw specs and the app produces polished, consistent descriptions using a chat completion call.

### [Real-Time Streaming Responses](scenarios/streaming-responses.md) ([repo](https://github.com/dotnet/ai-samples/tree/main/src/microsoft-extensions-ai/))

A customer service web app where AI responses appear word-by-word in the chat window, mimicking a human typing. The ASP.NET backend streams tokens via Server-Sent Events to the React frontend, giving users immediate feedback even for long, detailed responses.

### [Structured Data Extraction](scenarios/structured-data-extraction.md) ([repo](https://github.com/dotnet/ai-samples/tree/main/src/microsoft-extensions-ai/))

A legal tech company that processes incoming contracts. The system extracts party names, dates, obligations, and termination clauses from PDF text into a strongly-typed `ContractSummary` object, which is then stored in a database and surfaced in dashboards.

### [Text Classification and Categorization](scenarios/text-classification.md) ([repo](https://github.com/dotnet/ai-samples/tree/main/src/microsoft-extensions-ai/))

A customer support platform that automatically triages incoming tickets. Each ticket is classified by intent (billing, technical, account, feedback) and urgency (critical, high, normal, low). The classification drives automatic routing to the appropriate team queue.

## Developer Tooling

### [Pre-built Agent Runtime](scenarios/prebuilt-agent-runtime.md) ([repo](https://github.com/github/copilot-sdk))

An internal dev platform that helps engineers scaffold services, review code against company standards, and automate migrations.

## Edge and Device AI

### [Edge and Device Inference](scenarios/edge-device-inference.md) ([repo](https://github.com/microsoft/onnxruntime/tree/main/csharp/sample/))

A manufacturing quality-inspection app running on factory-floor tablets classifies product images in real time using an ONNX model. No cloud connectivity is needed, and inference completes in under 50ms per image.

## Enterprise Model Management

### [Managed AI Infrastructure](scenarios/managed-ai-infrastructure.md) ([repo](https://github.com/azure-samples/aistudio-python-quickstart-sample))

A financial services company that needs centrally managed models with content filtering, audit logs, and the ability to swap models without redeploying applications.

## Interoperability

### [Expose APIs to AI Models](scenarios/expose-apis-to-ai.md) ([repo](https://github.com/modelcontextprotocol/csharp-sdk/tree/main/samples/))

An internal engineering platform that exposes database queries, deployment tools, and monitoring dashboards as MCP tools. Any AI assistant in the organization can discover and use them.

## Local Development

### [Docker-Based Local Inference](scenarios/docker-local-inference.md) ([repo](https://docs.docker.com/ai/model-runner/))

A development team building a microservices application that includes AI features. Their existing `docker-compose.yml` already defines the API, database, and message queue. They add Docker Model Runner as another service, and the AI model starts alongside everything else with `docker compose up`.

### [Local Development with Foundry Local](scenarios/local-dev-foundry.md) ([repo](https://github.com/dotnet/ai-samples/tree/main/src/microsoft-extensions-ai/))

A financial services team building an AI compliance assistant. Regulatory requirements prohibit sending data to external services during development. Foundry Local runs the same Phi-3 model locally that will run on Azure AI Foundry in production, ensuring consistent behavior without data leaving the developer's machine.

### [Local Development with Ollama](scenarios/local-dev-ollama.md) ([repo](https://github.com/dotnet/ai-samples/tree/main/src/microsoft-extensions-ai/))

A startup building an AI-powered writing assistant. During development, the team runs Phi-3 via Ollama on their laptops — no API keys, no costs, no data leaving the machine. In CI and production, the same code targets Azure OpenAI's GPT-4o. The switch is a single configuration change.

## Migration

### [Migrate from Semantic Kernel](scenarios/migrate-from-semantic-kernel.md) ([repo](https://learn.microsoft.com/agent-framework/migration-guide/from-semantic-kernel/))

A customer support application originally built with Semantic Kernel plugins and planners. The team migrates simple chat completions to MEAI's `IChatClient` and replaces SK's agent orchestration with MAF agents, reducing complexity while gaining access to the latest features.

## Search and Retrieval

### [Semantic Search and RAG](scenarios/semantic-search.md) ([repo](https://github.com/dotnet/ai-samples/tree/main/src/microsoft-extensions-vector-data/))

An HR portal where employees ask natural-language questions about company policies. Documents are ingested as embeddings into a vector store, and the system retrieves relevant policy sections to ground its answers.

## Tool Integration

### [Tool Calling and Function Invocation](scenarios/tool-calling.md) ([repo](https://github.com/dotnet/ai-samples/tree/main/src/microsoft-extensions-ai/))

A support chat that can look up order status and check return policies. The AI reasons about the user's question, decides which tool to call, and synthesizes the answer from real data.
