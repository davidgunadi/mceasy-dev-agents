# McEasy Claude Agents

AI-powered document writing pipelines for McEasy's product, IoT, and strategy teams. Built on Claude Code using a multi-agent system that handles research, writing, C-level simulation, and auditing automatically.

---

## What's in here

Three slash commands, each triggering a full pipeline:

| Command | What it produces |
|---|---|
| `/prd` | Product Requirements Document |
| `/doe` | Hardware Design of Experiment |
| `/prfaq` | PR/FAQ (Amazon Working Backwards format) |

Each pipeline runs 4 agents in sequence: **Researcher → Writer → C-Level Shield → Auditor**, then pauses for your review.

---

## Prerequisites

- [Claude Desktop](https://claude.ai/download) installed
- Claude Code enabled (comes with Claude Pro or Max)
- This repo cloned to your machine

---

## Setup

**Option A — Clone the repo** (recommended if you have Git)
```bash
git clone https://github.com/mceasy/mceasy-dev-agents.git
```

**Option B — Download as ZIP** (no Git required)
1. Go to the repo on GitHub
2. Click the green **Code** button → **Download ZIP**
3. Unzip the file on your machine

Then:

1. Open the folder in Claude Code via Claude Desktop

2. That's it — the agents and skills load automatically from `.claude/`

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
- **The loop runs until you're satisfied** — just stop when you're happy with the output

### Tips

- The more context you give at the start, the better the Researcher output will be
- You can upload a rough `.md` file with bullet points — the Researcher will make sense of it
- If the Auditor flags something you disagree with, tell Claude and it will skip that issue

---

## Pipeline detail

```
You: "I want to write a PRD for X"
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
```

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

---

## Questions

Reach out to Dave (CTO) or your squad tech lead.
