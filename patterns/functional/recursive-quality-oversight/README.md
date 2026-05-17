---
id: PATTERN-002
title: "Recursive Quality Oversight"
title_ru: "Паттерн 2. «Активная прослеживаемость: Агент-Аудитор» (Recursive Quality Oversight)"
type: pattern
subtype: functional
status: raw
source: "author's development"
date_added: 2026-05-07
version: 1.0
---

# Recursive Quality Oversight

> **Паттерн 2. «Активная прослеживаемость: Агент-Аудитор» (Recursive Quality Oversight)**

**Problem:** Passive auditing — storing logs and recording errors — does not prevent problems; it merely documents what has already happened. By the time an error is discovered, it has already propagated through several pipeline stages and produced a cascade of defective artifacts. A mechanism is needed that actively searches for root causes rather than merely logging symptoms.

**Solution:** A specialized meta-agent — the Auditor — is introduced, which observes the pipeline's operation "from the outside." The Auditor periodically analyzes interaction logs, identifies root causes of errors (not just their symptoms), and surfaces improvement recommendations for the Architect. Key extensions: (1) the Auditor is equipped with data drift detection capability; (2) the Auditor compares computed projections with ground-truth facts, detecting the "smooth wall effect" — when explicit contradictions disappear in the final text instead of being explicitly flagged.

**Example:** When analyzing a series of similar defects in finished code, the Auditor discovers that the root cause is not in the developer's work but in systematic ambiguity at the functional requirements stage: the template is missing a mandatory "Data Type" field. The Auditor proposes that the Architect add this field to the FR template and update the Few-Shot examples for the analyst agent.

**Experimental Verification:** Deliberately introduce ambiguity into one of the requirements at the User Story stage. Trace how this ambiguity transforms through the FR and TS. Verify: whether the Auditor identifies the specific stage where the distortion occurred and formulates a concrete proposal for fixing the template.

**Application History:** Not applied. This section is populated based on real-world use of the pattern: task context, what worked, what required adjustment, and final conclusions.
