---
title: Expose APIs to AI Models
job: I need to expose my app's capabilities to AI models and agents
category: Interoperability
technologies:
  - MCP
status: GA
repo: https://github.com/modelcontextprotocol/csharp-sdk/tree/main/samples/
---

# Expose APIs to AI Models

> Make your APIs discoverable and callable by any AI system

## Why MCP

MCP is an open protocol that standardizes how applications expose tools, data, and context to AI models. Build an MCP server in .NET, and any MCP-compatible client — Copilot, Claude, custom agents — can discover and invoke your tools. This is the interoperability layer.

## Architecture

```
Your .NET backend → MCP server (tools, resources, prompts)
  → Any MCP client (Copilot, Claude, MAF agent, custom)
```

## Example

An internal engineering platform that exposes database queries, deployment tools, and monitoring dashboards as MCP tools. Any AI assistant in the organization can discover and use them.

## Code

```csharp
builder.Services.AddMcpServer()
    .WithTools<DatabaseTools>()
    .WithTools<DeploymentTools>();
```

## MCP + MAF

MAF agents can consume MCP servers as tool sources, giving your agents access to any MCP-compatible service.
