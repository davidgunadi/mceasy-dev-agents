---
name: prfaq
description: Start a new PR/FAQ document pipeline for McEasy. Invoke this when the user wants to write a PR/FAQ using Amazon's Working Backwards format, adapted for McEasy's context.
---

Greet the user and explain the pipeline before starting:

"Saya akan membantu kamu menulis PR/FAQ menggunakan format Amazon Working Backwards, yang sudah kami adaptasi untuk McEasy:

1. 🔍 **Researcher** (Opus) — Riset problem di market, validasi customer need, dan benchmark kompetitor
2. ✍️ **PR/FAQ Writer** (Sonnet) — Menulis PR/FAQ lengkap sesuai format McEasy (dengan perbaikan dari format Amazon original)
3. 🛡️ **C-Level Shield** (Sonnet) — Mensimulasikan pertanyaan sulit dari CEO, COO, CFO, CTO, dan CBO
4. 🔎 **Auditor** (Sonnet) — Review kualitas dokumen, kedalaman FAQ, metrik sukses, dan customer quote

Sebelum kita mulai — jawab beberapa pertanyaan ini:
- Fitur atau produk apa yang ingin dibuat PR/FAQ-nya?
- Problem customer apa yang diselesaikan?
- Ada customer spesifik yang sudah request atau validasi ini?
- Siapa target user utamanya?"

Once the user responds, invoke the @researcher agent with all context. Then follow this pipeline in strict order:
1. @researcher → validates problem, researches customer need and market
2. @prfaq-writer → produces full PR/FAQ document
3. @c-level-shield → simulates C-level hard questions
4. @auditor → reviews full document

## McEasy PR/FAQ Template Structure
The @prfaq-writer must follow this structure, fixing the gaps vs Amazon's original format:

### 📰 Press Release
- **Headline**: One punchy line — what launched, for whom, why it matters
- **Subheadline**: One sentence expanding the headline
- **Body paragraph 1**: Who is this for and what can they now do?
- **Body paragraph 2**: What was the problem before? (Be specific — name the pain)
- **Body paragraph 3**: How does the solution work? (Not too technical)
- **Customer Quote**: MANDATORY. A specific, emotional, named quote from a real customer persona (e.g. "Budi, Fleet Manager at JBL"). Never leave this blank.
- **Feature bullet list**: 3–5 key capabilities
- **Availability**: When and how customers get access, pricing

### 📸 Visuals
- Figma link or placeholder with description of what visual is needed

### ❓ External FAQs (minimum 6 questions)
Must cover:
- Who is this for?
- What problem does it solve?
- How does it work? (step by step)
- What are the benefits?
- How is this different from what exists today?
- When can customers access it?
- Is there an additional cost?
- What happens if [edge case]?

### ❓ Internal FAQs (minimum 5 questions)
Must cover:
- Why now? (market timing)
- Which validated customers need this?
- What are the dependencies?
- What are the risks and mitigations?
- How does this align with McEasy's strategic priorities?
- What is the estimated engineering effort?

### 📊 Key Metrics
MANDATORY — must be filled, not left blank. Include:
- Primary adoption metric with % target and timeframe
- Secondary business metric (revenue, churn, NPS)
- Owner for each metric

### 💡 One-Sentence Vision
MANDATORY — must be a sharp, compelling single sentence that sells the feature. Not a placeholder.

## Important notes for @prfaq-writer:
- Write the press release in PAST TENSE as if the feature already launched — this forces clarity on what exactly shipped
- Customer quotes must be specific and emotional, never generic
- All metrics must have numbers and timeframes
- The one-sentence vision must be complete and compelling

After auditor completes, pause and show results. Loop back to @prfaq-writer if issues found, until user is satisfied.
