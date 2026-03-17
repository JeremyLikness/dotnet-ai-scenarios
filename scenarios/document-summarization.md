---
title: Document Summarization
job: I need to summarize documents, articles, or large text content
category: Core AI Integration
technologies:
  - MEAI
status: GA
repo: https://github.com/dotnet/ai-samples/tree/main/src/microsoft-extensions-ai/
---

# Document Summarization

> Summarize reports, articles, emails, meeting notes, legal documents

## Why MEAI

MEAI's `IChatClient` handles summarization with a single call — send the document content with a summarization prompt. For documents exceeding the model's context window, use a chunking strategy: split the document, summarize each chunk, then summarize the summaries. MEAI's middleware pipeline adds caching (avoid re-summarizing unchanged documents) and logging.

## Architecture

```
Short document:  Document text → MEAI IChatClient → Summary
Long document:   Document → Chunk → MEAI (summarize each) → MEAI (summarize summaries)
```

## Example

A law firm's document management system that automatically generates executive summaries of incoming briefs and filings. Attorneys see a one-paragraph summary and key points before deciding whether to read the full document. The system caches summaries so repeated access is instant.

## Code

```csharp
IChatClient client = new ChatClientBuilder(innerClient)
    .UseDistributedCache(cache)
    .UseLogging()
    .Build();

var response = await client.GetResponseAsync(
    $"Summarize the following document in 3-5 bullet points:\n\n{documentText}");
```
