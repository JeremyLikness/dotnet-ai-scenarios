---
title: Multi-Agent Coordination
job: I need multiple AI agents to cooperate on complex tasks
category: Agent Orchestration
technologies:
  - MAF
  - MEAI
status: RC
repo: https://github.com/microsoft/agent-framework/tree/main/dotnet/samples/
---

# Multi-Agent Coordination

> Supervisor/worker patterns, agent handoffs, parallel agent execution, specialized sub-agents

## Why MAF

MAF provides first-class support for multi-agent patterns. A supervisor agent can delegate to specialized sub-agents, handle handoffs between them, and aggregate results. Each agent has its own tools, instructions, and state — but MAF manages the coordination, error recovery, and audit trail. This is the production-grade approach for complex workflows that exceed what a single agent can handle.

## Architecture

```
User request → MAF supervisor agent
  ├── Sub-agent: Triage (classify, route)
  ├── Sub-agent: Specialist A (domain logic + tools)
  ├── Sub-agent: Specialist B (different domain)
  └── Sub-agent: Reviewer (validate, approve)
  → Aggregated response with full reasoning trail
```

## Example

An enterprise HR platform where a supervisor agent routes employee requests to specialized sub-agents: one handles benefits questions (with access to benefits APIs), another handles PTO requests (with calendar and approval tools), and a third handles IT provisioning (with Active Directory and ticketing tools). The supervisor manages handoffs and ensures each request reaches the right specialist.

## Code

```csharp
var supervisor = AgentBuilder.CreateSupervisor()
    .WithSubAgent(triageAgent)
    .WithSubAgent(benefitsAgent)
    .WithSubAgent(ptoAgent)
    .WithSubAgent(itAgent)
    .Build();
```
