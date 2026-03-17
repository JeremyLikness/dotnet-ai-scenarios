---
title: Local Development with Ollama
job: I need to develop and test AI features locally without cloud costs
category: Local Development
technologies:
  - Ollama
  - MEAI
status: GA
repo: https://github.com/dotnet/ai-samples/tree/main/src/microsoft-extensions-ai/
---

# Local Development with Ollama

> Zero-cost local development, offline AI, privacy-sensitive prototyping

## Why Ollama + MEAI

Ollama runs open-source models (Llama, Phi, Mistral, Gemma, and more) locally on your machine with a simple CLI. MEAI's provider-agnostic abstractions mean your code is identical whether targeting Ollama locally or Azure OpenAI in production — only the endpoint configuration changes. This gives you free, offline, private AI development with zero cloud dependency.

## Architecture

```
Development: Your app → MEAI IChatClient → Ollama (local, free)
Production:  Your app → MEAI IChatClient → Azure OpenAI (cloud, scaled)
                        (same code, different config)
```

## Example

A startup building an AI-powered writing assistant. During development, the team runs Phi-3 via Ollama on their laptops — no API keys, no costs, no data leaving the machine. In CI and production, the same code targets Azure OpenAI's GPT-4o. The switch is a single configuration change.

## Code

```csharp
// Development — Ollama
IChatClient client = new OllamaChatClient(new Uri("http://localhost:11434"), "phi3");

// Production — Azure OpenAI (same IChatClient interface)
// IChatClient client = new AzureOpenAIClient(endpoint, credential)
//     .GetChatClient("gpt-4o")
//     .AsIChatClient();

var response = await client.GetResponseAsync("Improve this paragraph...");
```

## Notes

- Install Ollama: `curl -fsSL https://ollama.com/install.sh | sh` (Linux/macOS) or download from [ollama.com](https://ollama.com)
- Pull a model: `ollama pull phi3`
- Ollama runs on CPU by default; GPU acceleration available with CUDA/Metal
