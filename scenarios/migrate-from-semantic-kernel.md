---
title: Migrate from Semantic Kernel
job: I need to migrate my existing Semantic Kernel application to the current stack
category: Migration
technologies:
  - MEAI
  - MAF
status: GA
repo: https://learn.microsoft.com/agent-framework/migration-guide/from-semantic-kernel/
---

# Migrate from Semantic Kernel

> SK to MEAI for simple calls, SK to MAF for agent orchestration

## Why MEAI + MAF

Semantic Kernel is in maintenance mode — security fixes only, no new features. The recommended migration paths are:

| Your SK usage | Migrate to | What changes |
|---|---|---|
| Simple AI calls (chat, completions, embeddings) | **MEAI** | Replace `Kernel` with `IChatClient`. Simpler API, same capabilities. |
| Agent orchestration (plugins, planners, multi-step) | **MAF** | Replace SK agents with MAF agents. Tested patterns for supervisor/worker, handoffs. |
| SK + MEVD connectors | **MEVD standalone** | MEVD providers are migrating out of the SK namespace. Use standalone packages. |

## Architecture

```
Before: Your app → Semantic Kernel (Kernel, plugins, planners) → AI provider
After:  Your app → MEAI (IChatClient, tools) → AI provider
        Your app → MAF (agents, orchestration) → MEAI → AI provider
```

## Example

A customer support application originally built with Semantic Kernel plugins and planners. The team migrates simple chat completions to MEAI's `IChatClient` and replaces SK's agent orchestration with MAF agents, reducing complexity while gaining access to the latest features.

## Notes

- **Timeline:** Plan to migrate within 6–12 months
- **Official migration guide:** [SK → MAF migration](https://learn.microsoft.com/agent-framework/migration-guide/from-semantic-kernel/)
- MAF uses MEAI under the hood, so all MEAI knowledge carries forward
