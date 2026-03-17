---
title: Agent Orchestration
job: I need to build an agent with multi-step orchestration, routing, and workflows
category: Agent Orchestration
technologies:
  - MAF
  - MEAI
status: RC
repo: https://github.com/microsoft/agent-framework/tree/main/dotnet/samples/
---

# Agent Orchestration

> Customer support agents, claims processing, approval workflows, multi-agent systems

## Why MAF

MAF gives you a framework for agent orchestration that you own, test, and deploy. It handles tool routing, multi-turn state, error recovery, and multi-agent coordination. Unlike hand-rolling orchestration with MEAI alone, MAF provides tested patterns for supervisor/worker agents, handoffs, and audit trails. It uses MEAI under the hood, so all your existing MEAI knowledge carries forward.

## Architecture

```
User request → MAF agent (orchestration, state, routing)
  → Tool calls via MEAI
  → Sub-agent delegation (MAF multi-agent)
  → Structured response with audit trail
```

## Example

An insurance claims agent that triages submissions, routes to specialist agents (auto, property, health), and produces recommendations with full reasoning chains.

## Key Differentiator

MAF agents are .NET code. You test them with xUnit. You deploy them anywhere .NET runs. You debug them with breakpoints. This is the production-grade story for business-critical agent logic.
