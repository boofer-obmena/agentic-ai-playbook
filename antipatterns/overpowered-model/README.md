---
id: ANTIPATTERN-001
title: "Overpowered Model Anti-Pattern"
title_ru: "Антипаттерн. «Избыточная мощность модели» (Overpowered Model Anti-Pattern)"
type: antipattern
status: applied
subtype: "antipattern"
source: "author's development; applied on Mac Mini (April 2026)"
date_added: 2026-05-07
version: 1.0
related: ["PATTERN-010", "PATTERN-025"]
---

# Overpowered Model Anti-Pattern

> **Антипаттерн. «Избыточная мощность модели» (Overpowered Model Anti-Pattern)**

**Problem:** A common misconception: the more powerful the model, the better the agent. In practice, a model whose capabilities exceed the role's requirements begins to exhibit undesirable initiative: interprets instructions more broadly than intended, independently makes decisions beyond the role's scope, modifies files and configurations without an explicit request, and finds clever workarounds around restrictions.

**How It Manifests:** The agent does "more than asked" — updates files the request never touched. The agent changes its own configuration or rules without confirmation. The agent ignores prohibitions by finding workarounds. The agent asks fewer clarifying questions and acts more often on its own assumptions.

**Solution:** Match the model to the task level, not to the maximum possible capability. For routine executor agents (system administrator, backup, monitoring) — a mid-tier model with `think: false`. For analytical and review agents — the same or a slightly more powerful model with `think: true`. Rule: try a less powerful model first — upgrade only if the task quality target is not met.

**Relationship to Other Patterns:** PATTERN-010 (Agent Tool Manifest) — physically restricting tools reduces the risk but does not eliminate the problem: a smart model will find an available tool for the undesirable action. PATTERN-025 (Three-Level Rules Architecture) — explicit prohibitions in the system prompt work better with a less powerful model.

**Experimental Verification:** Run the same agent with the same prompt on two models: a frontier-class model and a mid-tier one. Assign a task with deliberately fuzzy boundaries. Measure: the number of actions not explicitly requested; the number of file changes not specified in the task; accuracy in following prohibitions.

**Application History:** Identified during operation of the Mac Mini server administrator agent (April 2026). The frontier-class model exhibited undesirable initiative. After replacing it with `qwen3:14b` (`think: false`), behavior stabilized. The rule "match the model to the task level" has been adopted as an agent design standard.
