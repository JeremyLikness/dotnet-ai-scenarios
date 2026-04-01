# .NET AI Decision Guide

> A community-driven guide helping .NET developers choose the right Microsoft AI technologies for their scenarios.

## Purpose

Microsoft offers a layered set of AI technologies for .NET — from low-level abstractions to full agent platforms. They compose together rather than compete, but knowing where to start can be overwhelming.

This repository captures real-world scenarios to help you answer:

1. **What am I trying to build?** → Browse [jobs to be done](jobs-to-be-done.md)
2. **Which technologies do I need?** → Follow the [decision flow](decision-flow.md) or read the [scenario files](scenarios/)
3. **What does this look like in practice?** → See the [examples](examples.md)

## Getting Started

There are two ways to use this repository: **browse on GitHub** or **use the Copilot CLI locally**.

### Option 1: Browse on GitHub

Navigate the files directly:

- **[jobs-to-be-done.md](jobs-to-be-done.md)** — Start here. Find the "I need to..." statement that matches your goal.
- **[categories.md](categories.md)** — Browse by technology area (e.g., Agent Orchestration, Content Safety).
- **[examples.md](examples.md)** — See real-world examples grouped by category.
- **[scenarios/](scenarios/)** — Read individual scenario files for full details, architecture, and code.

### Option 2: Use with GitHub Copilot CLI

Clone the repo and use the Copilot CLI to explore scenarios interactively, ask questions, and even add new scenarios through conversation.

```bash
# 1. Clone the repository
git clone https://github.com/<owner>/dotnet-ai.git
cd dotnet-ai

# 2. Launch GitHub Copilot CLI
gh copilot

# 3. Start asking questions
```

**Example prompts you can use:**

| What you want to do | Example prompt |
|---|---|
| Find the right technology | *"I need to add semantic search to my .NET app. What should I use?"* |
| Explore a category | *"Show me all scenarios related to agent orchestration"* |
| Understand a technology | *"When should I use MAF vs MEAI with function calling?"* |
| Compare approaches | *"What's the difference between using MCP and building tools directly in MAF?"* |
| Add a new scenario | *"I want to add a new scenario for real-time streaming with AI agents"* |
| Check what's available | *"What jobs to be done are covered in this repo?"* |

When adding a new scenario via the CLI, Copilot will walk you through all the required fields, validate your input, and create the scenario file. You can then commit and open a PR.

**What if your scenario doesn't exist yet?** If you ask a question and no matching scenario is found, Copilot will still give you its best recommendation — and then offer to help you turn your question into a new scenario. It will walk you through the required fields one at a time (job statement, category, technologies, example, code/repo, etc.) and create the file for you. Every question is a potential contribution.

> **Tip:** Copilot understands the full structure of this repository via [`.github/copilot-instructions.md`](.github/copilot-instructions.md). It knows the rules, required fields, approved technologies, and can help you create properly formatted scenario files.

## Repository Structure

```
dotnet-ai/
├── README.md                          # You are here
├── jobs-to-be-done.md                 # All "I need to..." statements (auto-generated)
├── examples.md                        # All examples across scenarios (auto-generated)
├── categories.md                      # All categories (auto-generated)
├── scenarios/                         # One markdown file per scenario
│   ├── single-ai-capability.md
│   ├── semantic-search.md
│   └── ...
└── .github/
    ├── copilot-instructions.md        # Copilot CLI context (rules, format, tech list)
    ├── ISSUE_TEMPLATE/                # Issue template for new scenarios
    └── workflows/                     # Automation for processing contributions
```

### Scenario Files

Each scenario is a self-contained markdown file in the `scenarios/` folder. Every scenario follows a consistent structure defined by its YAML front matter and body:

| Field | Required | Description |
|---|---|---|
| `title` | ✅ | Short, descriptive title |
| `job` | ✅ | The "I need to..." statement — what the developer is trying to accomplish |
| `category` | ✅ | Grouping category (e.g., "Content Safety", "Agent Orchestration") |
| `technologies` | ✅ | List of recommended Microsoft technologies |
| `status` | ✅ | Maturity status (GA, RC, Preview, Experimental) |
| `repo` | ✅* | GitHub repository URL demonstrating the scenario |

*\*Either `repo` or an inline **Code** section is required. Both are encouraged.*

The body of each file includes:

- **Why** — rationale for the technology recommendation
- **Architecture** — how the pieces connect (text or diagram)
- **Example** — a concrete, real-world scenario description
- **Code** — a short code sample or reference to the related repo

### Rollup Files

These files are **auto-generated** from the scenario files. Do not edit them directly:

- **[jobs-to-be-done.md](jobs-to-be-done.md)** — Every "I need to..." statement, linked to its scenario
- **[examples.md](examples.md)** — Every example, grouped by category
- **[categories.md](categories.md)** — Every category with its associated scenarios

## Contributing

There are three ways to contribute a new scenario:

### Method 1: GitHub Issue (Recommended for most users)

1. **Open an issue** using the [New Scenario template](.github/ISSUE_TEMPLATE/new-scenario.yml)
2. **Fill in all required fields** — job statement, category, technologies, example, repo/code, etc.
3. **Submit the issue** — the automation will:
   - Validate your submission for completeness and consistency
   - Create a scenario markdown file in `scenarios/`
   - Update the rollup files (jobs-to-be-done, examples, categories)
   - Open a PR with all changes
4. **Review the PR** — if the submission needs work, the automation will comment with specific errors on the issue. Edit the issue to fix them and it will re-run.

### Method 2: Copilot CLI (Recommended for interactive exploration)

1. **Clone the repo and launch Copilot CLI:**
   ```bash
   git clone https://github.com/<owner>/dotnet-ai.git
   cd dotnet-ai
   gh copilot
   ```
2. **Tell Copilot what you want to add:**
   ```
   I want to add a new scenario for building a RAG pipeline with content safety filters.
   ```
3. **Copilot will guide you** through the required fields, validate your input, and create the scenario file with proper front matter and structure.
4. **Commit and push:**
   ```bash
   git checkout -b scenario/my-new-scenario
   git add .
   git commit -m "Add scenario: Content-Safe RAG Pipeline"
   git push origin scenario/my-new-scenario
   ```
5. **Open a PR** on GitHub. The rollup files will be regenerated automatically.

### Method 3: Direct PR

If you're comfortable with the format, create a scenario file directly:

1. Copy an existing file from `scenarios/` as a template
2. Fill in all required front matter fields and body sections
3. Submit a PR — rollup files will be regenerated automatically

### Scenario Format Rules

When submitting a new scenario, follow these rules:

1. **Job statements start with "I need to..."** — they describe what the developer wants to accomplish, not how
2. **Categories use title case** — e.g., "Enterprise Model Management", not "enterprise model management"
3. **Technologies must be from the approved list** (see below)
4. **Examples must be concrete** — describe a specific app/system, not an abstract concept
5. **One scenario per file** — if a scenario covers multiple jobs, split it into separate submissions
6. **Every scenario needs a code reference** — either a `repo` URL in front matter, an inline code sample, or both
7. **New categories are welcome** — if none of the existing categories fit, propose a new one using Title Case

### Approved Technologies

| Technology | Abbreviation | Status |
|---|---|---|
| Microsoft.Extensions.AI | MEAI | GA |
| Microsoft.Extensions.VectorData | MEVD | GA |
| Model Context Protocol (C# SDK) | MCP | GA |
| Microsoft Agent Framework | MAF | RC |
| GitHub Copilot SDK | Copilot SDK | Technical Preview |
| Azure AI Foundry | Foundry | GA |
| Foundry Local | Foundry Local | GA |
| .NET Aspire | Aspire | GA |
| ONNX Runtime | ONNX | GA |
| Ollama | Ollama | GA |
| Docker Model Runner | Docker MR | GA |

### Editing an Existing Scenario

Submit a PR directly against the scenario file, or use the Copilot CLI to make changes interactively. Rollup files will be regenerated automatically.

## License

This project is licensed under the [MIT License](LICENSE).
