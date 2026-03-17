---
title: Docker-Based Local Inference
job: I need containerized local model inference that fits my Docker workflow
category: Local Development
technologies:
  - Docker Model Runner
  - MEAI
  - Aspire
status: GA
repo: https://docs.docker.com/ai/model-runner/
---

# Docker-Based Local Inference

> Containerized models, Docker Compose integration, Aspire orchestration

## Why Docker Model Runner + MEAI

Docker Model Runner brings local model inference into your existing Docker workflow. If your team already uses Docker Compose for local development, Model Runner adds AI models as just another container. Aspire can orchestrate it alongside your other services. MEAI code is unchanged — same `IChatClient`, different endpoint.

## Architecture

```
Docker Compose / Aspire AppHost
  ├── Your API (ASP.NET container)
  ├── Database (PostgreSQL container)
  ├── Docker Model Runner (AI model container)
  └── Other services...
Your app → MEAI IChatClient → Docker Model Runner endpoint
```

## Example

A development team building a microservices application that includes AI features. Their existing `docker-compose.yml` already defines the API, database, and message queue. They add Docker Model Runner as another service, and the AI model starts alongside everything else with `docker compose up`.

## Notes

- Fits naturally into Docker-based development workflows
- Aspire can orchestrate Model Runner alongside your other services
- Same MEAI code works against Docker Model Runner, Ollama, or cloud providers
