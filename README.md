# AIOPS — AI Orchestration & Optimization Protocol

**An approval-first AI agent skill for model selection, token optimization, tool discovery, and verifiable execution.**

AIOPS is a reusable twelve-stage workflow for AI-assisted product, business, and technical work. It helps an assistant choose suitable models, skills, MCP servers, and connectors; assess security and cost; obtain explicit approval; and validate the result.

Created by [Hesham Hammam](https://github.com/heshamhammam1).

## Install AIOPS

### Coding agents: one command

Requires Node.js 22.20 or later and access to GitHub. Run from the project where you want the skill:

```bash
npx skills add heshamhammam1/AIOPS-AI-Orchestration-Optimization-Protocol --skill aiops
```

The installer lets you choose a supported agent. Installation is project-scoped by default; use `-g` only if you want it available across projects.

For Claude Code without interactive agent selection:

```bash
npx skills add heshamhammam1/AIOPS-AI-Orchestration-Optimization-Protocol --skill aiops --agent claude-code
```

The project-scoped Claude Code installation was tested on 5 November 2026 using the Skills CLI. The installed skill file matched the published source. Other agent targets have not been tested for this release.

### Claude web or desktop: upload the ZIP

1. Open [release v1.0.1](https://github.com/heshamhammam1/AIOPS-AI-Orchestration-Optimization-Protocol/releases/tag/v1.0.1) and download **aiops.zip** from Assets.
2. In Claude, open **Customize → Skills**, choose **+ → Create skill → Upload a skill**, and upload the ZIP.
3. Enable the skill. Availability depends on your account and organization settings.

The ZIP contains `aiops/SKILL.md` and `aiops/LICENSE`. Use this asset rather than GitHub's automatically generated source-code archives.

### Other tools: manual installation

Copy the entire `aiops` folder into your tool's documented skills directory. Consult that tool's instructions; paths and activation behavior vary.

### Verify activation

Start a fresh conversation or session if your host requires it, then ask:

> Apply AIOPS. I want you to review a product requirement. First recommend the model, tools, scope, risks, and validation plan. Wait for my approval before doing the review.

Expected behavior: the assistant presents an AIOPS recommendation and asks for approval before substantive work. This is a user-run behavioral check; the installation test did not establish compliance across models or hosts.

### Versions and updates

Use the versioned ZIP when you need the exact v1.0.1 package. The repository install command follows the repository's current source. Review changes before updating. Installation never grants approval for future tasks.

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
