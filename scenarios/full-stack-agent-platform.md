---
title: Full-Stack Agent Platform
job: I need to build a production agent system with multiple services, data, and enterprise infrastructure
category: Cloud-Native Operations
technologies:
  - MAF
  - MEAI
  - MEVD
  - MCP
  - Azure AI Foundry
  - Aspire
status: RC
repo: https://github.com/dotnet/aspire-samples
---

# Full-Stack Agent Platform

> Multi-service agent systems with knowledge bases, tool interop, enterprise model management, and full observability

## Why the Full Stack

When your agent system is the product — not just a feature — you need the full .NET AI stack working together. MAF handles agent orchestration, MEAI provides the AI abstractions, MEVD powers the knowledge base, MCP exposes and consumes tools, Foundry manages models, and Aspire ties it all together with orchestration, health checks, and distributed tracing.

## Architecture

```
Aspire AppHost
  ├── API gateway (ASP.NET)
  ├── MAF supervisor agent → sub-agents (support, billing, escalation)
  │     └── Tools via MEAI function calling
  ├── MCP server (exposes internal APIs to any AI client)
  ├── MEVD → Azure AI Search (knowledge base)
  └── Model endpoint → Azure AI Foundry (managed, compliant)
All services wired, traced via OpenTelemetry, health-checked
```

## Example

An insurance company building a claims processing platform. A supervisor agent triages incoming claims and routes to specialist agents (auto, property, health). Each specialist has access to domain-specific tools (policy lookup, damage assessment APIs) and a knowledge base of claim guidelines. MCP servers expose the platform's capabilities to other internal AI assistants. Aspire orchestrates all services and provides end-to-end distributed tracing from user submission through agent reasoning to claim resolution.

## Notes

- Start with a single agent (MAF + MEAI) and add layers as complexity grows
- Aspire's local development experience means all services run on your machine
- Each technology layer is independently testable
