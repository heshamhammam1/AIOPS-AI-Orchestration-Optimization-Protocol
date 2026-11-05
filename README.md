# AIOPS — AI Orchestration & Optimization Protocol

**An approval-first AI agent skill for model selection, token optimization, tool discovery, and verifiable execution.**

AIOPS is a reusable twelve-stage workflow for AI-assisted product, business, and technical work. It helps an assistant choose suitable models, skills, MCP servers, and connectors; assess security and cost; obtain explicit approval; and validate the result.

Created by [Hesham Hammam](https://github.com/heshamhammam1).

## Install and use AIOPS

| Platform | Method | Scope |
| --- | --- | --- |
| Claude Code | Skills CLI or manual skill folder | Project or personal |
| Claude web / desktop | Upload the release ZIP | Account, subject to settings |
| Codex CLI / local app | Skills CLI or manual skill folder | Project or personal |
| Ollama | Local Modelfile with AIOPS as the system prompt | Named local model configuration |
| Grok | Paste the protocol in chat, or load it as API system instructions | Conversation or application |

Read the [Limited Use License](LICENSE) before use. Keep the license with private copies. These instructions do not grant permission to publicly redistribute AIOPS or publish a model package containing it.

### Claude Code

With Node.js 22.20 or later installed, run from your project:

```bash
npx skills add heshamhammam1/AIOPS-AI-Orchestration-Optimization-Protocol --skill aiops --agent claude-code
```

For manual installation, download and extract the [v1.0.1 release ZIP](https://github.com/heshamhammam1/AIOPS-AI-Orchestration-Optimization-Protocol/releases/tag/v1.0.1). Copy the entire extracted `aiops` folder, including `LICENSE`, to one location:

- Project: `.claude/skills/aiops/`
- Personal, across local projects: `~/.claude/skills/aiops/`

Do not overwrite an existing installation without reviewing it. Start a new session and invoke `/aiops` with your task. Local folder installation does not by itself install a skill into your Claude web account or Cowork.

### Claude web and desktop

1. Download **aiops.zip** from the [v1.0.1 release](https://github.com/heshamhammam1/AIOPS-AI-Orchestration-Optimization-Protocol/releases/tag/v1.0.1).
2. Open **Customize → Skills**, choose **+ → Create skill → Upload a skill**, and upload the ZIP.
3. Enable AIOPS, then start a conversation and ask it to apply AIOPS before your task.

The ZIP contains `aiops/SKILL.md` and `aiops/LICENSE`. Use this asset rather than GitHub's automatic source-code ZIP. Skill availability depends on account capabilities and organization policy.

### Codex CLI and local app

With Node.js 22.20 or later installed, run from your project:

```bash
npx skills add heshamhammam1/AIOPS-AI-Orchestration-Optimization-Protocol --skill aiops --agent codex
```

Alternatively, extract the release ZIP and copy its complete `aiops` folder to:

- Project: `.agents/skills/aiops/`
- Personal, across local projects: `~/.agents/skills/aiops/`

Start a fresh Codex session, select the skill if your interface provides a skill picker, or explicitly ask: “Use the aiops skill before this task.”

These are local filesystem instructions. Managed ChatGPT Work or cloud environments can have separate installation and sharing flows; copying a folder on your computer does not automatically install it there.

### Ollama: local system-prompt configuration

This route loads AIOPS as instructions; it does not install a native skill loader or add tools, connectors, or approval enforcement.

Prerequisites: Ollama running locally, Python 3, and a base model already installed. Run `ollama list` and choose an exact model name you have available.

Extract the release ZIP. In the directory containing the extracted `aiops` folder, run the following Python code, replacing `YOUR_INSTALLED_MODEL` with that model name:

```python
from pathlib import Path

base_model = "YOUR_INSTALLED_MODEL"
skill = Path("aiops/SKILL.md").read_text(encoding="utf-8")
body = skill.split("---", 2)[2].strip()
if '"""' in body:
    raise ValueError("Review triple-quote escaping before generating the Modelfile.")
Path("Modelfile.aiops").write_text(
    f'FROM {base_model}\nSYSTEM """\n{body}\n"""\n',
    encoding="utf-8",
)
```

Then run:

```bash
ollama create aiops-local -f Modelfile.aiops
ollama run aiops-local
```

Ask it to apply AIOPS and wait for approval before your task. Keep the license alongside your local configuration. This creates a local configuration; it does not train a model. Do not publicly push or redistribute the configuration containing AIOPS without permission. Instruction following depends on the model and context capacity.

### Grok: conversation or API instructions

**Grok chat:** open `aiops/SKILL.md`, copy the protocol from the heading onward (omit the YAML block between the opening `---` delimiters), and paste it into a new conversation. Add:

> Treat the preceding AIOPS protocol as instructions for this conversation, subject to your platform rules. Before my next task, present an AIOPS recommendation and wait for explicit approval. Do not assume access to tools you do not have.

Then send your task. Re-supply the protocol in a new conversation; do not assume it persists across chats. This is prompt-based use, not a verified native Grok skill installation.

**Grok API applications:** read the protocol body from the local file and include it as a `system` message in the application's xAI Responses API input:

```python
from pathlib import Path

protocol = Path("aiops/SKILL.md").read_text(encoding="utf-8")
protocol = protocol.split("---", 2)[2].strip()
input_messages = [
    {"role": "system", "content": protocol},
    {"role": "user", "content": "Review my requirement. Recommend a plan first."},
]
# Supply input_messages as input to your configured xAI Responses API call.
```

This snippet prepares messages; it does not make an API call. Configure authentication securely outside chat and choose a model available to your account. Maintain these instructions in the application's conversation handling. Enforce consequential approvals in application code if required; a system prompt alone is not a permission boundary.

### Verify activation on any platform

Ask:

> Apply AIOPS. I want you to review a product requirement. First recommend the model, tools, scope, risks, and validation plan. Wait for my approval before doing the review.

Expected behavior: a recommendation and approval request before substantive work. Check that it does not invent tool access or claim to switch models automatically.

### Validation and updates

The Claude Code CLI installation was tested on 5 November 2026 and its installed `SKILL.md` matched the published source. Codex, Ollama, Grok, and Claude ZIP-upload steps are documentation-backed instructions, not end-to-end tests performed for this repository. No paid API requests were made.

Use the versioned ZIP for the exact v1.0.1 package. CLI installation follows current repository source. Review updates before installing; installation does not approve future tasks.

### Official platform references

- [Claude Code skills](https://code.claude.com/docs/en/skills)
- [Claude skill uploads](https://support.claude.com/en/articles/12512180-use-skills-in-claude)
- [OpenAI: build skills and Codex locations](https://learn.chatgpt.com/docs/build-skills)
- [Ollama Modelfile reference](https://docs.ollama.com/modelfile)
- [xAI text generation and system messages](https://docs.x.ai/developers/model-capabilities/text/generate-text)
- [Vercel Skills CLI](https://github.com/vercel-labs/skills)

## Get started

Read the complete [AIOPS skill](aiops/SKILL.md). Download or clone this repository and import the `aiops` folder into a host that supports `SKILL.md` skills, following that host’s installation instructions. For other assistants, supply the file as task instructions where supported.

Publishing or downloading this repository does not automatically install the skill, connect accounts, or change an AI model. Tool access and model availability depend on the host environment. AIOPS is a procedural instruction set, not a technical permission boundary.

Example prompt:

> Apply AIOPS before reviewing this product requirement. Recommend an efficient model and reasoning effort, identify suitable skills and connectors, define the scope and validation plan, and wait for my approval before execution.

## What AIOPS covers

- AI model selection and reasoning effort matched to task complexity.
- Token and context optimization through targeted retrieval and bounded execution.
- Discovery of installed skills, Model Context Protocol (MCP) servers, and connectors.
- Source trust, privacy, least privilege, and read/write impact assessment.
- Explicit approval for a defined scope before substantive execution.
- Deliverable validation, safe recovery, and reusable learning.

## The twelve-stage workflow

| Stage | Action |
| --- | --- |
| 1 | Understand the task and success criteria. |
| 2 | Retrieve the minimum relevant context. |
| 3 | Classify complexity and risk. |
| 4 | Recommend an efficient model and reasoning effort. |
| 5 | Discover suitable skills, MCP servers, and connectors. |
| 6 | Assess security and permissions. |
| 7 | Optimize execution and the token budget. |
| 8 | Request explicit approval. |
| 9 | Execute only the approved scope. |
| 10 | Validate deliverables and evidence. |
| 11 | Recover safely from failure. |
| 12 | Capture reusable learnings. |

## Example applications

| Task | AIOPS contribution |
| --- | --- |
| Product requirements and user stories | Define deliverables, retrieve project decisions, recommend tools, and validate acceptance criteria. |
| Sprint and backlog reviews | Bound the review scope and distinguish proposed changes from approved updates. |
| Technical analysis | Match reasoning effort to complexity and define evidence and validation requirements. |
| Connector or skill adoption | Assess trust, access scopes, duplication, and setup burden before installation. |

These are intended uses, not claims of benchmarked performance or guaranteed savings.

## Repository contents

- [`aiops/SKILL.md`](aiops/SKILL.md): authoritative protocol, approval template, operational principles, and completion report.
- `README.md`: overview and usage guidance.

## Governance and privacy

Host system instructions, platform controls, and safety rules take precedence. Approval applies only to the described scope; material changes require renewed approval. Never include credentials or confidential company or customer information in public contributions.

AIOPS here means **AI Orchestration & Optimization Protocol**. It is distinct from the common use of “AIOps” for artificial intelligence for IT operations.

## Source and contributions

The protocol was supplied by Hesham Hammam on 5 November 2026. The skill preserves that wording and all twelve stages; changes to the supplied source are limited to YAML frontmatter and Markdown formatting.

Use GitHub issues to suggest improvements and pull requests to propose focused changes. Explain the problem, expected behavior, and how the proposed change was checked. Do not include private project details.

## License

Copyright © 2026 Hesham Hammam. All rights reserved except as granted in the [AIOPS Limited Use License](LICENSE).

Installation, personal use, and internal business use are permitted under its terms. Redistribution, resale, and public hosting of the Materials or modified versions require separate written permission, except as permitted by the license, applicable law, or GitHub’s Terms of Service. Public GitHub forks remain permitted under those terms.

This is a custom limited-use license, not an open-source license. A copy is included in the skill folder and the v1.0.1 ZIP. It has not been independently reviewed by legal counsel. The earlier v1.0.0 release is retained unchanged; its ZIP does not contain this license.
