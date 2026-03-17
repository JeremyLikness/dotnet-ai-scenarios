---
title: Text Classification and Categorization
job: I need to classify or categorize text inputs automatically
category: Core AI Integration
technologies:
  - MEAI
status: GA
repo: https://github.com/dotnet/ai-samples/tree/main/src/microsoft-extensions-ai/
---

# Text Classification and Categorization

> Sentiment analysis, intent detection, ticket routing, content tagging

## Why MEAI

MEAI's `IChatClient` with structured output makes classification straightforward — define your categories as a C# enum or class, and the model returns a typed result. For high-throughput scenarios, pair with MEAI's caching middleware to avoid re-classifying identical inputs. For latency-sensitive or offline scenarios, consider ONNX Runtime with a fine-tuned classification model.

## Architecture

```
Input text → MEAI IChatClient (structured output) → Category/label
High-volume: Input text → MEAI (with cache middleware) → Category/label
Offline/edge: Input text → ONNX Runtime (fine-tuned model) → Category/label
```

## Example

A customer support platform that automatically triages incoming tickets. Each ticket is classified by intent (billing, technical, account, feedback) and urgency (critical, high, normal, low). The classification drives automatic routing to the appropriate team queue.

## Code

```csharp
public enum TicketCategory { Billing, Technical, Account, Feedback }
public enum Urgency { Critical, High, Normal, Low }

public record TicketClassification(TicketCategory Category, Urgency Urgency, string Reason);

var result = await client.GetResponseAsync<TicketClassification>(
    $"Classify this support ticket:\n\n{ticketText}");

Console.WriteLine($"Route to: {result.Result.Category} ({result.Result.Urgency})");
```
