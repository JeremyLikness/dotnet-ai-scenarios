---
title: Structured Data Extraction
job: I need to extract structured data from unstructured text
category: Core AI Integration
technologies:
  - MEAI
status: GA
repo: https://github.com/dotnet/ai-samples/tree/main/src/microsoft-extensions-ai/
---

# Structured Data Extraction

> Parse invoices, extract entities, convert natural language to typed objects, form processing

## Why MEAI

MEAI's `IChatClient` supports structured output via JSON schema constraints. You define a C# type, and the model returns a strongly-typed object extracted from unstructured text. Combined with MEAI's middleware (logging, retries, caching), this gives you a reliable pipeline for turning free-form text into structured data without writing custom parsers.

## Architecture

```
Unstructured text → MEAI IChatClient (with JSON schema / structured output)
  → Model extracts fields → Strongly-typed C# object
```

## Example

A legal tech company that processes incoming contracts. The system extracts party names, dates, obligations, and termination clauses from PDF text into a strongly-typed `ContractSummary` object, which is then stored in a database and surfaced in dashboards.

## Code

```csharp
var response = await client.GetResponseAsync<ContractSummary>(
    $"Extract the contract details from this text:\n\n{contractText}");

Console.WriteLine($"Parties: {response.Result.PartyA} and {response.Result.PartyB}");
Console.WriteLine($"Effective date: {response.Result.EffectiveDate}");
```
