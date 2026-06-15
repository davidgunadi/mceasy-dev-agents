---
name: prd
description: Start a new PRD writing pipeline using McEasy's 4-agent system. Invoke this when the user wants to write a PRD for any McEasy product feature.
---

Greet the user and explain the pipeline before starting:

"I'll help you write a PRD using McEasy's 4-agent pipeline:

1. 🔍 **Researcher** (Opus) — Researches the Indonesian & SEA market, benchmarks competitors, and produces a research brief
2. ✍️ **PRD Writer** (Sonnet) — Writes the full PRD based on the research brief, following the McEasy template
3. 🛡️ **C-Level Shield** (Sonnet) — Simulates hard questions from CEO, COO, CFO, CTO, CBO, and CDSO
4. 🔎 **Auditor** (Sonnet) — Reviews the full document: PRD quality, ISO 27001, B2B SaaS, infrastructure, scalability, and hardware
5. 📄 **Confluence Formatter** — Converts the approved document into a paste-ready HTML file for Confluence

Before we start — tell me about the feature you want to build, or upload a .md file with notes and context you already have. The more context you give me, the better the research output will be.

If you already have some initial ideas, answer these questions:
- What feature do you want to build?
- What problem does it solve?
- Are there any customers or users who have already requested this?
- Are there any technical or business constraints to consider?"

Once the user responds or uploads a file, invoke the @researcher agent with all provided context. Then follow this pipeline in strict order:
1. @researcher → produces research brief
2. @prd-writer → receives research brief, produces full PRD
3. @c-level-shield → receives full PRD, appends Q&A section
4. @auditor → reviews complete document including Q&A, produces audit report

After the auditor completes, pause and present the audit results to the user. Ask whether to proceed with fixes or if they are satisfied.

- If there are issues: loop back to @prd-writer with the fix direction, then re-run @c-level-shield and @auditor. Repeat until the user is satisfied.
- Once the user confirms they are happy with the document: say "Great — generating your Confluence-ready HTML file now..." and immediately invoke @confluence-formatter to convert the final document into an HTML file.
