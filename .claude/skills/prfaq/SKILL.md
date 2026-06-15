---
name: prfaq
description: Start a new PR/FAQ document pipeline for McEasy. Invoke this when the user wants to write a PR/FAQ using Amazon's Working Backwards format, adapted for McEasy's context.
---

Greet the user and explain the pipeline before starting:

"I'll help you write a PR/FAQ using Amazon's Working Backwards format, adapted for McEasy:

1. 🔍 **Researcher** (Opus) — Researches the problem in the market, validates customer need, and benchmarks competitors
2. ✍️ **PR/FAQ Writer** (Sonnet) — Writes the full PR/FAQ following McEasy's format with Amazon's hard requirements enforced
3. 🛡️ **C-Level Shield** (Sonnet) — Simulates hard questions from CEO, COO, CFO, CTO, CBO, and CDSO
4. 🔎 **Auditor** (Sonnet) — Reviews document quality, FAQ depth, success metrics, and customer quote

Before we start — answer a few questions:
- What feature or product do you want to write a PR/FAQ for?
- What customer problem does it solve?
- Are there specific customers who have already requested or validated this?
- Who is the primary target user?"

Once the user responds, invoke the @researcher agent with all context. Then follow this pipeline in strict order:
1. @researcher → validates problem, researches customer need and market
2. @prfaq-writer → produces full PR/FAQ document
3. @c-level-shield → simulates C-level hard questions
4. @auditor → reviews full document

## Amazon Hard Requirements
The @prfaq-writer must enforce these — all are non-negotiable:
1. Press release written in past tense as if already launched
2. Customer quote is mandatory, specific, named — never a placeholder
3. One-sentence vision is mandatory and must be sharp and complete
4. Key metrics must be filled with numbers and timeframes — no TBD
5. Minimum 6 external FAQs covering objections, pricing, alternatives, edge cases
6. Minimum 5 internal FAQs covering why now, validated customers, dependencies, risks, strategic alignment

After auditor completes, pause and show results. Loop back to @prfaq-writer if issues found, until user is satisfied.
