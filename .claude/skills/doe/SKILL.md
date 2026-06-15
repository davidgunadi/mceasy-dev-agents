---
name: doe
description: Start a new Hardware Design of Experiment (DoE) document pipeline for McEasy's IoT team. Invoke this when the user wants to create a DoE for a new hardware device, firmware validation, or benchmark comparison.
---

Greet the user and explain the pipeline before starting:

"I'll help you write a Hardware DoE document using McEasy's 4-agent pipeline:

1. 🔍 **Researcher** (Opus) — Researches device specs, benchmarks competitor hardware, and provides IoT market context for Indonesia & SEA
2. ✍️ **DoE Writer** (Sonnet) — Writes the full DoE document following the McEasy IoT team template
3. 🛡️ **C-Level Shield** (Sonnet) — Simulates hard questions from CEO, COO, CFO, CTO, CBO, and CDSO on the hardware decision
4. 🔎 **Auditor** (Sonnet) — Reviews the document: test case completeness, success criteria, hardware constraints, and commercial viability

Before we start — answer a few questions:
- What device or hardware is being tested in this DoE?
- Is this a new device evaluation, a benchmark between devices, or firmware validation?
- What is the comparison device (if any)?
- Do you already have specific test cases planned?
- What is the target timeline for this DoE?"

Once the user responds, invoke the @researcher agent with the hardware context. Then follow this pipeline in strict order:
1. @researcher → researches device specs, market context, competitor hardware
2. @doe-writer → produces full DoE document following McEasy template
3. @c-level-shield → simulates C-level questions on hardware investment decisions
4. @auditor → reviews for test case completeness, success criteria clarity, commercial considerations

## McEasy DoE Template Structure
The @doe-writer must follow this exact structure based on McEasy's actual DoE format:

- **Approval** (checkboxes for Grady Kusmulyadi and Raymond Sutjiono)
- **Background and Purpose** (What, Why, How)
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
