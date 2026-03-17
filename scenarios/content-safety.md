---
title: Content Safety and Moderation
job: I need to filter AI inputs and outputs for safety, compliance, and content policy
category: Content Safety
technologies:
  - Azure AI Foundry
  - MEAI
status: GA
repo: https://github.com/dotnet/ai-samples/tree/main/src/microsoft-extensions-ai/
---

# Content Safety and Moderation

> Prompt injection defense, harmful content filtering, PII detection, content policy enforcement

## Why Azure AI Foundry + MEAI

Azure AI Foundry provides built-in content safety filters at the platform layer — content filtering, prompt shield, groundedness detection, and PII redaction. These run automatically on Foundry-hosted models without code changes. For additional application-level filtering, MEAI's middleware pipeline lets you add custom safety checks as middleware that runs before and after every AI call.

## Architecture

```
User input → MEAI middleware (custom safety checks)
  → Azure AI Foundry endpoint (built-in content filters)
  → Model inference
  → Foundry content filters (output)
  → MEAI middleware (post-processing checks)
  → Safe response to user
```

## Example

A healthcare company deploying a patient-facing chatbot. Foundry's content filters block harmful medical advice and PII exposure at the platform layer. A custom MEAI middleware component additionally checks responses against an approved medical knowledge base to prevent hallucinated treatment recommendations.

## Code

```csharp
IChatClient client = new ChatClientBuilder(foundryClient)
    .Use(async (messages, options, next, ct) =>
    {
        // Pre-call: check for prompt injection patterns
        ValidateInput(messages);

        var response = await next(messages, options, ct);

        // Post-call: verify response against policy
        ValidateOutput(response);
        return response;
    })
    .UseLogging()
    .Build();
```
