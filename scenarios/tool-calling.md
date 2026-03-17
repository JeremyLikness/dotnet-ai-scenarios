---
title: Tool Calling and Function Invocation
job: I need my app to take actions — look things up, call APIs, make decisions
category: Tool Integration
technologies:
  - MEAI
status: GA
repo: https://github.com/dotnet/ai-samples/tree/main/src/microsoft-extensions-ai/
---

# Tool Calling and Function Invocation

> Tool calling, function invocation, multi-step reasoning

## Why MEAI with Function Calling

MEAI's function calling middleware lets you define .NET methods as tools that the AI model can invoke. The middleware handles the tool-call loop automatically — the model decides which tool to call, MEAI executes it, and feeds the result back. This is sufficient for single-agent scenarios with a handful of tools.

## Architecture

```
User question → MEAI chat client (with tool definitions)
  → Model selects tool → MEAI invokes your .NET method → result fed back → final answer
```

## Example

A support chat that can look up order status and check return policies. The AI reasons about the user's question, decides which tool to call, and synthesizes the answer from real data.

## Code

```csharp
var tools = new[]
{
    AIFunctionFactory.Create(LookupOrder),
    AIFunctionFactory.Create(CheckReturnPolicy)
};

IChatClient agent = new ChatClientBuilder(innerClient)
    .UseFunctionInvocation()
    .Build();
```

## When to Graduate to MAF

When you have more than a handful of tools, need multi-agent coordination, want structured error recovery, or the orchestration logic itself is your business logic.
