# McEasy Claude Agents — CLAUDE.md

This repo contains McEasy's AI-powered document writing system built on Claude Code. It uses a multi-agent pipeline to produce PRDs, Hardware DoEs, and PR/FAQs — with built-in research, writing, C-level simulation, auditing, and Confluence export.

---

## Agents

There are 7 agents in `.claude/agents/`. Each has a specific role and runs in a defined order:

| Agent | Model | Role |
|---|---|---|
| `researcher` | Opus | Researches the topic, benchmarks SEA market and competitors, produces a research brief |
| `prd-writer` | Sonnet | Writes the full PRD following McEasy's template |
| `doe-writer` | Sonnet | Writes the full Hardware DoE following McEasy's IoT team template |
| `prfaq-writer` | Sonnet | Writes the full PR/FAQ following Amazon's Working Backwards format |
| `c-level-shield` | Sonnet | Simulates hard questions from CEO, COO, CFO, CTO, CBO, and CDSO |
| `auditor` | Sonnet | Reviews the full document for quality, ISO 27001, B2B SaaS, infrastructure, scalability, and hardware constraints |
| `confluence-formatter` | Sonnet | Converts the approved document into a clean HTML file ready to paste into Confluence |

---

## Skills (Slash Commands)

There are 3 skills in `.claude/skills/`. Trigger them by typing the slash command in Claude Code:

| Command | What it produces |
|---|---|
| `/prd` | Product Requirements Document |
| `/doe` | Hardware Design of Experiment |
| `/prfaq` | PR/FAQ (Amazon Working Backwards) |

---

## Pipeline Order

All three pipelines follow the same agent sequence. Never skip or reorder steps.

```
User input / .md file upload
        ↓
  @researcher (Opus)
        ↓
  @[prd-writer / doe-writer / prfaq-writer] (Sonnet)
        ↓
  @c-level-shield (Sonnet)
        ↓
  @auditor (Sonnet)
        ↓
  ⏸ Pause — show audit results to human
        ↓
  Human reviews and confirms fix direction
        ↓
  Loop back to writer if issues found
        ↓
  Human confirms they are happy
        ↓
  @confluence-formatter (Sonnet)
        ↓
  .html file ready to paste into Confluence
```

---

## Rules

- Always invoke `@researcher` first before any writer agent
- Always invoke `@c-level-shield` before `@auditor`
- The auditor always reviews the full document including the C-Level Shield Q&A section
- After the auditor completes, always pause and show results to the user — never auto-proceed
- The loop runs until the human is satisfied — there is no automatic exit
- Once the human confirms they are happy, automatically invoke `@confluence-formatter` — do not wait for a separate command
- All documents are produced in English only

---

## McEasy Context

- B2B SaaS telematics and logistics platform based in Indonesia
- Products: GPS tracking, TrackVision (AI dashcam with DMS/ADAS), fleet management, 3PL logistics
- ISO 27001 certified, AWS infrastructure
- Serves vehicle owners, 3PL operators, and transportation vendors
- Co-founders: CEO Raymond Sutjiono, CFO Hendrik Ekowaluyo, CTO Dave Gunadi
- C-Level team simulated by `c-level-shield`: CEO, COO, CFO, CTO, CBO, CDSO
