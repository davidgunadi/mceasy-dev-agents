# McEasy Claude Agents

AI-powered document writing pipelines for McEasy's product, IoT, and strategy teams. Built on Claude Code using a multi-agent system that handles research, writing, C-level simulation, auditing, and Confluence export automatically.

---

## What's in here

Three slash commands, each triggering a full pipeline:

| Command | What it produces |
|---|---|
| `/prd` | Product Requirements Document |
| `/doe` | Hardware Design of Experiment |
| `/prfaq` | PR/FAQ (Amazon Working Backwards format) |

Each pipeline runs 5 steps: **Researcher → Writer → C-Level Shield → Auditor → Confluence Formatter**

---

## Prerequisites

- Claude Code enabled (comes with Claude Pro or Max)
- One of the following:
  - [Claude Desktop](https://claude.ai/download) with Claude Code, or
  - [VS Code](https://code.visualstudio.com/) with the [Claude Code extension](https://marketplace.visualstudio.com/items?itemName=anthropic.claude-code)
- This repo cloned to your machine

---

## Setup

1. Clone the repo
```bash
git clone https://github.com/mceasy/mceasy-dev-agents.git
```

2. Open the folder in Claude Code via Claude Desktop

3. That's it — the agents and skills load automatically from `.claude/`

> **Note:** The `.claude/` folder is hidden by default. On Mac press `Cmd + Shift + .` to show hidden files. On Windows go to View → Show → Hidden items.

---

## How to use

### Starting a pipeline

Type the slash command in Claude Code and hit Enter:

```
/prd
/doe
/prfaq
```

Claude will greet you, explain the pipeline, and ask about the feature or device you want to document. You can either describe it in chat or upload a `.md` file with your notes.

### During the pipeline

- The agents run automatically in sequence
- After the **Auditor** completes, the pipeline **pauses** and shows you the audit results
- Review the issues, confirm the fix direction, and the writer will revise
- **The loop runs until you're satisfied** — just say you're happy when you're done
- Once you confirm, the **Confluence Formatter** runs automatically and produces an `.html` file

### Pasting into Confluence

1. Open the generated `.html` file in your browser
2. Press `Cmd+A` (Mac) or `Ctrl+A` (Windows) to select all
3. Press `Cmd+C` / `Ctrl+C` to copy
4. Open your Confluence page in Edit mode
5. Click in the editor and press `Cmd+V` / `Ctrl+V` to paste

Headings, tables, bullets, bold — all render correctly.

---

## Pipeline detail

```
You: describe feature or upload .md file
          ↓
    Researcher (Opus)
    Researches SEA market, competitors, user personas
          ↓
    Writer (Sonnet)
    Writes full document to McEasy template
          ↓
    C-Level Shield (Sonnet)
    Simulates CEO, COO, CFO, CTO, CBO, CDSO questions
          ↓
    Auditor (Sonnet)
    Reviews quality, ISO 27001, infra, scalability, hardware
          ↓
    ⏸ You review and decide what to fix
          ↓
    Loop until satisfied
          ↓
    Confluence Formatter (Sonnet)
    Generates paste-ready .html file
```

---

## Folder structure

```
mceasy-dev-agents/
├── CLAUDE.md                          # Project instructions — agents read this for context
├── README.md                          # This file
├── agent-flow.png                     # Pipeline diagram
├── outputs/                           # All generated files go here
└── .claude/
    ├── settings.local.json            # Local permissions (not committed)
    ├── agents/                        # One .md file per agent
    │   ├── researcher.md
    │   ├── prd-writer.md
    │   ├── doe-writer.md
    │   ├── prfaq-writer.md
    │   ├── c-level-shield.md
    │   ├── auditor.md
    │   └── confluence-formatter.md
    └── skills/                        # One folder per slash command
        ├── prd/
        │   └── SKILL.md              # /prd
        ├── doe/
        │   └── SKILL.md              # /doe
        └── prfaq/
            └── SKILL.md              # /prfaq
```

### How agents work

Each file in `.claude/agents/` defines one agent. The frontmatter controls how Claude uses it:

```markdown
---
name: agent-name            # How you invoke it: @agent-name
description: ...            # Claude reads this to decide when to use it
model: sonnet               # sonnet (fast) or opus (deep research)
tools: Read, Write          # What tools the agent can use
---

[System prompt — the agent's instructions and domain knowledge]
```

### How skills work

Each folder in `.claude/skills/` maps to a slash command. The folder name is the command:

```
.claude/skills/prd/SKILL.md   →   /prd
.claude/skills/doe/SKILL.md   →   /doe
```

The `SKILL.md` file is a prompt that tells Claude how to orchestrate the pipeline — which agents to invoke, in what order, and where to pause for human review.

### How CLAUDE.md works

`CLAUDE.md` in the repo root is always loaded as project context for every session. It defines:
- The pipeline order and rules
- McEasy product knowledge all agents share
- Hard rules (e.g. "all outputs go to `./outputs/`", "English only")

Agents inherit this context automatically — no need to repeat it in every agent file.

---

## Agents

| Agent | Model | Description |
|---|---|---|
| `researcher` | Opus | Market research, competitor benchmarking, SEA context |
| `prd-writer` | Sonnet | PRD using McEasy's standard template |
| `doe-writer` | Sonnet | Hardware DoE using McEasy's IoT team template |
| `prfaq-writer` | Sonnet | PR/FAQ using Amazon's Working Backwards format |
| `c-level-shield` | Sonnet | Hard questions from 6 C-level execs |
| `auditor` | Sonnet | 6-dimension document review |
| `confluence-formatter` | Sonnet | Converts final document to Confluence-ready HTML |

---

## Want to build your own pipeline?

A starter template is available in `template/` (or download `outputs/claude-agents-template.zip`). It includes:
- A blank `CLAUDE.md` with instructions for each section
- A template agent file (`.claude/agents/example-agent.md`)
- A template skill file (`.claude/skills/example-skill/SKILL.md`)
- A `settings.json` with safe default permissions
- The `outputs/` folder and `.gitignore`

Copy the `template/` folder, rename it, and replace the placeholders. The `README.md` inside explains every file.

---

## Questions

Reach out to Dave (CTO) or your squad tech lead.
