---
name: prd
description: Start a new PRD writing pipeline using McEasy's 4-agent system. Invoke this when the user wants to write a PRD for any McEasy product feature.
---

Greet the user and explain the pipeline before starting:

"Saya akan membantu kamu menulis PRD menggunakan pipeline 4-agent McEasy:

1. 🔍 **Researcher** (Opus) — Riset market Indonesia & SEA, benchmark kompetitor, dan membuat research brief
2. ✍️ **Writer** (Sonnet) — Menulis PRD lengkap berdasarkan research brief, mengikuti template McEasy
3. 🛡️ **C-Level Shield** (Sonnet) — Mensimulasikan pertanyaan sulit dari CEO, COO, CFO, CTO, dan CBO
4. 🔎 **Auditor** (Sonnet) — Review dokumen lengkap: kualitas PRD, ISO 27001, B2B SaaS, infrastruktur, skalabilitas, dan hardware

Sebelum kita mulai — ceritakan tentang fitur yang ingin kamu buat, atau upload file .md dengan catatan dan konteks yang sudah kamu punya. Semakin banyak konteks yang kamu berikan, semakin baik hasil researchnya.

Jika kamu sudah punya ide awal, jawab pertanyaan ini:
- Fitur apa yang ingin dibangun?
- Problem apa yang ingin diselesaikan?
- Ada customer atau user yang sudah request ini?
- Ada constraint teknis atau bisnis yang perlu dipertimbangkan?"

Once the user responds or uploads a file, invoke the @researcher agent with all provided context. Then follow this pipeline in strict order:
1. @researcher → produces research brief
2. @prd-writer → receives research brief, produces full PRD
3. @c-level-shield → receives full PRD, appends Q&A section
4. @auditor → reviews complete document including Q&A, produces audit report

After the auditor completes, pause and present the audit results to the user. Ask whether to proceed with fixes or if they are satisfied. Loop back to @prd-writer if issues need to be resolved, until the user decides to stop.
