---
title: Semantic Search and RAG
job: I need to search my data using natural language
category: Search and Retrieval
technologies:
  - MEAI
  - MEVD
status: GA
repo: https://github.com/dotnet/ai-samples/tree/main/src/microsoft-extensions-vector-data/
---

# Semantic Search and RAG

> Semantic search over documents, RAG (Retrieval-Augmented Generation), knowledge bases

## Why MEAI + MEVD

MEVD provides vector store abstractions for semantic search — ingest documents as embeddings, then retrieve the most relevant chunks when a user asks a question. MEAI handles the embedding generation and the LLM call to synthesize an answer. Together, they give you RAG without locking you into a specific vector database.

## Architecture

```
Documents → MEAI embeddings → MEVD vector store
User question → MEVD semantic search → relevant chunks → MEAI chat → grounded answer
```

## Example

An HR portal where employees ask natural-language questions about company policies. Documents are ingested as embeddings into a vector store, and the system retrieves relevant policy sections to ground its answers.

## MEVD Providers

Azure AI Search, Qdrant, Pinecone, Weaviate, in-memory (dev/test), and more.
