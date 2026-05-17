---
id: METHOD-004
title: "Constrained Templating with Evidence"
title_ru: "Принудительная шаблонизация с доказательным выводом (Constrained Templating with Evidence)"
type: method
status: raw
subtype: "method / technique"
source: "author's development"
date_added: 2026-05-07
version: 1.0-preview
---

# Constrained Templating with Evidence

> **Принудительная шаблонизация с доказательным выводом (Constrained Templating with Evidence)**

**Problem:** Without strict output format constraints, the LLM generates free-form narrative that is difficult to process automatically. When data is absent, the model tends to hallucinate — filling gaps with plausible but fabricated claims. In an agent pipeline, both phenomena lead to errors.

**Solution:** Each agent operates with a rigid output template, implemented through a combination of three mechanisms. JSON schema (structural contract): defines required fields, their types, and permitted values. Few-shot examples: several examples of correct output demonstrating the expected style and level of detail. Chain-of-Thought with evidence: for every claim, the agent must fill in an evidence field — a direct quotation or reference to a specific fragment of the input data from which the conclusion was drawn. When data is absent, the agent must explicitly state "Data unavailable" instead of generating assumptions.

**Example:** The analyst agent formulates functional requirements (FRs) based on a User Story. For each FR item, the evidence field contains an exact quotation from the User Story: "Basis: The user must be able to cancel an order within 24 hours of placement (User Story US-047, item 3)." The Auditor verifies: for every FR item, the evidence citation genuinely appears in the original User Story document.

**Experimental Verification:** Give the agent a task where some of the necessary data is deliberately missing (incomplete User Story). Verify: the agent does not hallucinate — it explicitly marks items for which data is absent as "Requires clarification." For the data that is present, all evidence fields contain correct references.

**Application History:** Not applied. This section is populated based on real-world use of the method: task context, what worked, what required adjustment, and final conclusions.

**When to Use:** [Requires author refinement — to be finalized in Phase 4]

**Limitations:** [Requires author refinement — to be finalized in Phase 4]

Related Patterns: [Requires author refinement — to be populated in Phase 4]
