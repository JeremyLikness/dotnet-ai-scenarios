---
title: Pre-built Agent Runtime
job: I need a pre-built agent runtime with planning, code awareness, and tool execution
category: Developer Tooling
technologies:
  - Copilot SDK
  - MEAI
  - MCP
status: Technical Preview
repo: https://github.com/github/copilot-sdk
---

# Pre-built Agent Runtime

> Developer tools, code-aware assistants, rapid agent prototyping

## Why GitHub Copilot SDK

The Copilot SDK embeds Copilot's full agent runtime — planning, multi-turn reasoning, file operations, MCP support, streaming — in your .NET application. You get a highly capable agent without building orchestration from scratch. Best suited for developer-facing tools and internal platforms where Copilot's code-awareness is an asset.

## Architecture

```
Your app → Copilot SDK (CopilotClient / CopilotSession)
  → Copilot agent runtime (planning, tool execution, MCP)
  → Custom tools registered via MEAI
```

## Example

An internal dev platform that helps engineers scaffold services, review code against company standards, and automate migrations.

## Important Considerations

- Requires Copilot CLI as a sidecar process (or BYOK with your own API keys)
- Best for internal/developer tools — not typically for end-user-facing products at scale
- Technical Preview status — APIs may evolve
