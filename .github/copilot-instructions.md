# Copilot Instructions for dotnet-ai

You are assisting with the **dotnet-ai** repository — a community-driven decision guide that helps .NET developers choose the right Microsoft AI technologies for their scenarios.

## Repository Purpose

This repo contains structured scenario files that map developer jobs-to-be-done ("I need to...") to recommended technology combinations from the Microsoft .NET AI stack. It is NOT a code repository — it is a curated knowledge base of markdown files.

## Repository Structure

```
dotnet-ai/
├── README.md                          # Rules, purpose, contribution guide
├── jobs-to-be-done.md                 # AUTO-GENERATED: all "I need to..." statements
├── examples.md                        # AUTO-GENERATED: all examples by category
├── categories.md                      # AUTO-GENERATED: all categories
├── scenarios/                         # One markdown file per scenario
│   ├── single-ai-capability.md
│   ├── semantic-search.md
│   └── ...
└── .github/
    ├── ISSUE_TEMPLATE/new-scenario.yml
    ├── workflows/process-issue.yml
    └── copilot-instructions.md        # This file
```

## Scenario File Format

Each scenario file in `scenarios/` has YAML front matter and a markdown body:

```markdown
---
title: Short Descriptive Title
job: I need to [what the developer wants to accomplish]
category: Category Name (Title Case)
technologies:
  - MEAI
  - MEVD
status: GA
repo: https://github.com/owner/repo-name
---

# Title

> One-line summary of the use cases this covers

## Why

Explain why the recommended technologies are the right fit.

## Architecture

Show how the pieces connect (text diagram preferred).

## Example

Describe a concrete, real-world scenario — a specific app or system.

## Code

```csharp
// Short code sample showing the key pattern
```

## Notes (optional)

Caveats, migration guidance, or links to docs.
```

### Required Fields

Every scenario MUST have:
- **title**: Short, descriptive
- **job**: Starts with "I need to"
- **category**: Title Case category name
- **technologies**: At least one from the approved list
- **status**: One of GA, RC, Technical Preview, Experimental
- **repo**: A GitHub repository URL or inline code sample demonstrating the scenario
- **Why** section in the body
- **Architecture** section in the body
- **Example** section in the body
- **Code** section in the body (may reference the repo instead of inline code)

### Approved Technologies

These are the only valid technology names for the `technologies` field:

- MEAI (Microsoft.Extensions.AI)
- MEVD (Microsoft.Extensions.VectorData)
- MCP (Model Context Protocol C# SDK)
- MAF (Microsoft Agent Framework)
- Copilot SDK (GitHub Copilot SDK)
- Azure AI Foundry
- Foundry Local
- Aspire (.NET Aspire)
- ONNX Runtime
- Ollama
- Docker Model Runner

### Categories

Categories are dynamically created from scenario files. Current categories include:
- Core AI Integration
- Search and Retrieval
- Tool Integration
- Agent Orchestration
- Interoperability
- Developer Tooling
- Enterprise Model Management
- Content Generation
- Content Safety
- Cloud-Native Operations
- Edge and Device AI
- Migration

New categories are welcome — just use a descriptive Title Case name.

## Rollup Files

The files `jobs-to-be-done.md`, `examples.md`, and `categories.md` are **auto-generated** from the scenario files. They are regenerated:
- When a new scenario is added via the issue workflow
- When scenarios are manually added or edited (via PR workflow)

**Never edit rollup files directly.** Always edit the source scenario files.

## How to Help Users

### When a user wants to explore scenarios:
1. Read the scenario files in `scenarios/` to understand what's available
2. Use `jobs-to-be-done.md` for a quick overview of all jobs
3. Use `categories.md` to find scenarios by technology area
4. Use `examples.md` to find concrete examples

### When a user wants to add a new scenario:
1. Ask them for the required fields: title, job, category, technologies, status, repo/code, why, architecture, example
2. Validate:
   - Job starts with "I need to"
   - Category is Title Case
   - Technologies are from the approved list
   - Example is concrete (specific app/system, not abstract)
   - A repo URL or code sample is provided
3. Create the scenario file in `scenarios/` with proper front matter
4. Remind them that rollup files will be auto-regenerated, or help regenerate them

### When a user wants to find the right technology:
1. Ask what they're trying to build (the "job")
2. Search existing scenarios for a match
3. If a matching scenario exists, present it with a link to the file
4. **If no matching scenario exists:**
   a. First, give your best recommendation based on the technology profiles below
   b. Then, tell the user: *"This scenario isn't in the guide yet. Want to add it so others can benefit?"*
   c. If they say yes, guide them through the scenario creation flow (see "When a user wants to add a new scenario" above) by asking for each required field one at a time:
      - Confirm or refine the **job** statement ("I need to...")
      - Ask which **category** fits, or propose one
      - Suggest **technologies** and confirm
      - Ask for the **status** of the primary technology
      - Ask for a **repo URL** or help them write a **code sample**
      - Ask them to describe a concrete **example** (specific app/system)
      - Ask for the **why** — or draft one based on the conversation and confirm
      - Ask for the **architecture** — or draft a text diagram and confirm
   d. Once all fields are gathered, create the scenario file in `scenarios/` with proper front matter
   e. Remind them to commit, push, and open a PR

   Technology recommendation profiles for when no scenario exists:
   - **MEAI** — any single AI call (chat, embeddings, classification, images)
   - **MEAI + MEVD** — semantic search, RAG
   - **MEAI + function calling** — tool invocation, API calls
   - **MAF + MEAI** — agent orchestration, multi-step workflows
   - **MCP** — exposing tools to AI models
   - **Copilot SDK** — developer tools, code-aware assistants
   - **Azure AI Foundry** — enterprise model management
   - **Aspire** — distributed service orchestration

### When a user asks a general question:
1. Answer the question using your knowledge of the .NET AI stack
2. Check whether the question maps to an existing scenario
3. If it does, link to the scenario file
4. If it doesn't, and the question represents a real developer job-to-be-done, offer to create a new scenario:
   *"That's a great question — and it's not covered by an existing scenario yet. Want me to help you add one?"*

### When a user wants to edit a scenario:
1. Help them identify the correct file in `scenarios/`
2. Ensure edits maintain the required format
3. Remind them to update front matter if the job, category, or technologies change

## Key Principles
- MEAI is always the foundation — every .NET AI app starts with it
- Technologies compose together, they don't compete
- Recommend incremental adoption: start simple, add layers as needed
- Model hosting (where it runs) is separate from application code (how you call it)
- Every scenario needs a working code reference (repo URL or inline sample)
- **Every question is a potential new scenario** — if a user asks about something not covered, help them contribute it back
