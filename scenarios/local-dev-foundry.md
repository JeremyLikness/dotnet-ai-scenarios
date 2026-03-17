---
title: Local Development with Foundry Local
job: I need production-parity local model inference during development
category: Local Development
technologies:
  - Foundry Local
  - MEAI
status: GA
repo: https://github.com/dotnet/ai-samples/tree/main/src/microsoft-extensions-ai/
---

# Local Development with Foundry Local

> Same model catalog as Azure AI Foundry, running on your machine

## Why Foundry Local + MEAI

Foundry Local gives you the same model catalog and APIs as cloud Azure AI Foundry, but running entirely on your dev machine. This means production-parity testing without cloud costs or network latency. Combined with MEAI, your code doesn't change between local and cloud — only the endpoint. Aspire can automate the toggle.

## Architecture

```
Development: Your app → MEAI IChatClient → Foundry Local (same models, local)
Production:  Your app → MEAI IChatClient → Azure AI Foundry (cloud, managed)
Aspire:      Toggle local ↔ cloud with configuration, not code
```

## Example

A financial services team building an AI compliance assistant. Regulatory requirements prohibit sending data to external services during development. Foundry Local runs the same Phi-3 model locally that will run on Azure AI Foundry in production, ensuring consistent behavior without data leaving the developer's machine.

## Code

```csharp
// Foundry Local uses the same OpenAI-compatible API
IChatClient client = new OpenAIClient("foundry-local-key",
        new OpenAIClientOptions { Endpoint = new Uri("http://localhost:5272") })
    .GetChatClient("phi-3")
    .AsIChatClient();

var response = await client.GetResponseAsync("Analyze this compliance report...");
```

## Notes

- Install: `winget install Microsoft.AI.Foundry.Local` (Windows) or see [docs](https://learn.microsoft.com/en-us/azure/ai-foundry/foundry-local/)
- List available models: `foundry model list`
- Same API shape as Azure OpenAI — seamless switch to cloud
