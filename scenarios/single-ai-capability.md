---
title: Add a Single AI Capability
job: I need to add a single AI capability to my existing app
category: Core AI Integration
technologies:
  - MEAI
status: GA
repo: https://github.com/dotnet/ai-samples/tree/main/src/microsoft-extensions-ai/
---

# Add a Single AI Capability

> Summarize text, classify inputs, generate embeddings, extract structured data

## Why MEAI

MEAI gives you provider-agnostic abstractions for chat completions, embeddings, tool calling, and image generation. The same code works against OpenAI, Azure OpenAI, Ollama, Foundry, and more. No orchestration overhead — just call the AI and use the result.

## Architecture

```
Your app → MEAI (IChatClient / IEmbeddingGenerator) → Any AI provider
```

## Example

An e-commerce app that generates product descriptions from catalog data. The product team enters raw specs and the app produces polished, consistent descriptions using a chat completion call.

## Code

```csharp
IChatClient client = new ChatClientBuilder(innerClient)
    .UseLogging()
    .Build();

var response = await client.GetResponseAsync("Summarize this document...");
```
