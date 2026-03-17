---
title: Conversational Chat Interface
job: I need to build a multi-turn conversational chat experience
category: Core AI Integration
technologies:
  - MEAI
status: GA
repo: https://github.com/dotnet/ai-samples/tree/main/src/microsoft-extensions-ai/
---

# Conversational Chat Interface

> Multi-turn chat, conversation history, system prompts, persona management

## Why MEAI

MEAI's `IChatClient` natively supports multi-turn conversations through message history. You manage the conversation as a list of messages (system, user, assistant) and pass the full history with each call. The middleware pipeline adds logging, caching, and telemetry without changing your conversation logic. Works with any provider — OpenAI, Ollama, Foundry, etc.

## Architecture

```
User message → Append to conversation history
  → MEAI IChatClient (full history) → AI provider
  → Assistant response → Append to history → Display to user
```

## Example

A SaaS platform adding an AI assistant sidebar to its dashboard. Users ask questions about their data, and the assistant maintains context across turns — remembering what was discussed, referring back to earlier questions, and refining its answers as the conversation progresses. A system prompt defines the assistant's persona and access boundaries.

## Code

```csharp
var history = new List<ChatMessage>
{
    new(ChatRole.System, "You are a helpful data analyst assistant.")
};

while (true)
{
    var userInput = Console.ReadLine();
    history.Add(new(ChatRole.User, userInput));

    var response = await client.GetResponseAsync(history);
    history.Add(new(ChatRole.Assistant, response.Text));

    Console.WriteLine(response.Text);
}
```
