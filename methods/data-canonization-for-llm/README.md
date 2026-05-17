---
id: METHOD-003
title: "Data Canonicalization for LLM"
title_ru: "Канонизация данных под модель (Data Canonicalization for LLM)"
type: method
status: raw
subtype: "method / technique"
source: "author's development"
date_added: 2026-05-07
version: 1.0-preview
---

# Data Canonicalization for LLM

> **Канонизация данных под модель (Data Canonicalization for LLM)**

**Problem:** Language models perform significantly more accurately with structured and unambiguous data formats than with natural language. "Five thousand rubles," "5000 rub.," "5K," and "5,000 RUB" all represent the same number, yet the model is forced to resolve the ambiguity each time. When processing large volumes of data, these errors accumulate.

**Solution:** At the preprocessing stage, all incoming data is converted into a canonical format. Numbers and amounts: "five thousand rubles" → "5,000 RUB." Dates and periods: "the last two years" → "2024-01-01 – 2025-12-31," "next quarter" → "2025-07-01 – 2025-09-30." Statuses and enumerations: "in progress," "pending approval," "with developer" → unified identifiers from the status reference. Roles and names: standardized spelling of system names, job titles, and domain terms. Canonicalized data does not replace the original — it is created additionally and fed to the LLM in place of the original.

**Example:** Query: "prepare a report for the last two quarters." The preprocessor canonicalizes the time period: "Q3 2024 (2024-07-01 – 2024-09-30) and Q4 2024 (2024-10-01 – 2024-12-31)." The analyst agent receives precise dates and formulates a database query without needing to compute the period boundaries independently.

**Experimental Verification:** Prepare a set of 20 queries containing amounts, dates, and time periods in natural language format. Process them in two modes: with canonization and without. Measure the percentage of correctly extracted numeric values and time periods in each mode.

**Application History:** Not applied. This section is populated based on real-world use of the method: task context, what worked, what required adjustment, and final conclusions.

**When to Use:** [Requires author refinement — to be finalized in Phase 4]

**Limitations:** [Requires author refinement — to be finalized in Phase 4]

Related Patterns: [Requires author refinement — to be populated in Phase 4]
