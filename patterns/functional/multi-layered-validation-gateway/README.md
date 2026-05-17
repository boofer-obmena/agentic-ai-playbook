---
id: PATTERN-005
title: "Multi-Layered Validation Gateway"
title_ru: "Паттерн 5. «Многоуровневый защитный контур (Валидатор)» (Multi-layered Validation Gateway)"
type: pattern
subtype: functional
status: raw
source: "author's development"
date_added: 2026-05-07
version: 1.0
---

# Multi-Layered Validation Gateway

> **Паттерн 5. «Многоуровневый защитный контур (Валидатор)» (Multi-layered Validation Gateway)**

**Problem:** Without explicit constraints, an agent can execute any operation without prior verification, leading to a breach of system integrity. A single check is insufficient: a syntactically correct operation may violate semantics, and a semantically correct one — business rules.

**Solution:** Every operation passes through a three-layer validation gateway: (1) Syntactic level — the operation conforms to the expected data schema. (2) Semantic level — the data is internally consistent. (3) Business rule level — the operation is permissible in the current context. An additional layer — "Data Contracts" (see Pattern 12): strict JSON schemas with field requirements, including a confidence score field.

**Example:** An agent attempts to hand off a task for testing without attaching a commit reference. The first and second levels pass. The third level blocks the operation: the business rule "Hand-off for testing requires at least one commit" is not satisfied. The agent receives a diagnostic message indicating the specific rule violated.

**Experimental Verification:** Prepare a set of 10 test operations: 7 correct and 3 with different types of violations. Success criteria: all 3 incorrect operations are blocked with precise diagnoses, all 7 valid operations are passed through with no false positives.

**Application History:** Not applied. This section is populated based on real-world use of the pattern: task context, what worked, what required adjustment, and final conclusions.
