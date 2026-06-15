---
name: doe
description: Start a new Hardware Design of Experiment (DoE) document pipeline for McEasy's IoT team. Invoke this when the user wants to create a DoE for a new hardware device, firmware validation, or benchmark comparison.
---

Greet the user and explain the pipeline before starting:

"Saya akan membantu kamu membuat dokumen HW DoE menggunakan pipeline McEasy:

1. 🔍 **Researcher** (Opus) — Riset spesifikasi teknis perangkat, benchmark kompetitor, dan konteks market hardware IoT di Indonesia & SEA
2. ✍️ **DoE Writer** (Sonnet) — Menulis dokumen DoE lengkap sesuai template McEasy IoT team
3. 🛡️ **C-Level Shield** (Sonnet) — Mensimulasikan pertanyaan sulit dari CEO, COO, CFO, CTO, dan CBO terkait keputusan hardware
4. 🔎 **Auditor** (Sonnet) — Review dokumen: kelengkapan test case, success criteria, hardware constraints, dan commercial viability

Sebelum kita mulai — jawab beberapa pertanyaan ini:
- Device / hardware apa yang akan di-DoE?
- Apakah ini pengujian device baru, benchmark antar device, atau validasi firmware?
- Device pembanding yang digunakan (jika ada)?
- Ada test case spesifik yang sudah kamu rencanakan?
- Timeline target DoE?"

Once the user responds, invoke the @researcher agent with the hardware context. Then follow this pipeline in strict order:
1. @researcher → researches device specs, market context, competitor hardware
2. @doe-writer → produces full DoE document following McEasy template
3. @c-level-shield → simulates C-level questions on hardware investment decisions
4. @auditor → reviews for test case completeness, success criteria clarity, commercial considerations

## McEasy DoE Template Structure
The @doe-writer must follow this exact structure based on McEasy's actual DoE format:

- **Approval** (checkboxes for Grady Kusmulyadi and Raymond Sutjiono)
- **Background and Purpose** (What, Why, How — in Bahasa Indonesia)
- **Current State** (existing hardware gaps and stakeholder needs)
- **Benefits** (Customer, Technical, Financial)
- **Commercial Consideration** (cost, cost vs capability, market acceptability)
- **Success Criteria** (measurable, clearly defined)
- **Estimated Timeline** (DoE execution, vendor review, commercial checklist, post-release review)
- **Test Case Summary** (table with #, Test Case, Objective, Type, Success Criteria, Timeline, Result)
- **Test Case Types**: Functional, Parameter, Stress, Power/Profiling
- **Vendor Documentation** (pinout, specs)
- **Detail of DoE** (one section per test case with: Objective, Hypothesis, Independent Variable, Dependent Variable, Control Variable, Equipment, Setup, Data Collection Result, Data Analysis, Summary)
- **Conclusion** (overall findings, critical failures if any)

After auditor completes, pause and show results to user. Loop back to @doe-writer if issues found, until user is satisfied.
