---
title: Service Orchestration and Observability
job: I need to orchestrate distributed AI services with observability
category: Cloud-Native Operations
technologies:
  - Aspire
status: GA
repo: https://github.com/dotnet/aspire-samples
---

# Service Orchestration and Observability

> Service orchestration, observability, local-to-cloud deployment

## Why .NET Aspire

Aspire is .NET's stack for cloud-native, observable, distributed applications. For AI apps, it orchestrates your services (API, agent, vector store, model endpoint), provides distributed tracing via OpenTelemetry, and manages the local ↔ cloud switch. It's the operations layer that makes everything production-ready.

## Architecture

```
Aspire AppHost
  ├── Your API (ASP.NET)
  ├── Agent service (MAF)
  ├── Vector store (MEVD → Azure AI Search or local)
  └── Model endpoint (Foundry Local or cloud)
All wired, traced, and health-checked automatically.
```

## Example

A multi-service support agent where Aspire ensures the API, agent, vector store, and model endpoint are all running, connected, and observable. Distributed tracing shows end-to-end request flow from user question through agent reasoning to model call and back.
