---
title: Real-Time Streaming Responses
job: I need to stream AI responses to users in real time
category: Core AI Integration
technologies:
  - MEAI
status: GA
repo: https://github.com/dotnet/ai-samples/tree/main/src/microsoft-extensions-ai/
---

# Real-Time Streaming Responses

> Token-by-token streaming, progressive UI updates, low perceived latency

## Why MEAI

MEAI's `IChatClient` supports streaming via `GetStreamingResponseAsync`, which yields response chunks as they arrive from the model. This dramatically reduces perceived latency — users see text appearing immediately instead of waiting for the full response. Works with any provider that supports streaming (OpenAI, Azure OpenAI, Ollama, Foundry).

## Architecture

```
User prompt → MEAI IChatClient.GetStreamingResponseAsync()
  → Token stream from AI provider
  → Progressive display (console, web UI via SignalR/SSE, etc.)
```

## Example

A customer service web app where AI responses appear word-by-word in the chat window, mimicking a human typing. The ASP.NET backend streams tokens via Server-Sent Events to the React frontend, giving users immediate feedback even for long, detailed responses.

## Code

```csharp
await foreach (var chunk in client.GetStreamingResponseAsync("Explain this error..."))
{
    Console.Write(chunk.Text);
}
```
