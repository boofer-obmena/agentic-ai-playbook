---
id: PATTERN-012
title: "Agent Boundary Contract"
title_ru: "Паттерн 12. «Контракт на границе как фейс-контроль агента» (Agent Boundary Contract)"
type: pattern
subtype: functional
status: raw
source: "author's development"
date_added: 2026-05-07
version: 1.0
---

# Agent Boundary Contract

> **Паттерн 12. «Контракт на границе как фейс-контроль агента» (Agent Boundary Contract)**

**Problem:** Language models can produce output in arbitrary formats: an essay instead of structured JSON, a lengthy explanation instead of a number. The next agent in the pipeline expects a specific format, and on mismatch either fails with an error or — worse — continues operating with incorrectly parsed data.

**Solution:** Every data hand-off boundary between agents is validated by the Orchestrator against a formally defined Contract that includes: a JSON schema with required fields and their types, business rules (permissible values for enumerated fields), and metadata requirements (including a mandatory `confidence` field — a numeric value representing the model's certainty). If the Contract is violated, the agent's output is rejected, and the agent receives a precise diagnosis of the mismatch.

**Example:** A QA agent generates free-form text instead of a structured format. The Orchestrator rejects the package: "Contract TestResult violated. Required fields missing: test_id, verdict."

**Experimental Verification:** Required. Prepare a set of 10 agent outputs: 7 complying with contract and 3 violating it in different ways. Success criteria: all 3 violations are blocked with precise diagnostics, all 7 valid outputs are passed through with no false positives.

**Application History:** Not applied. This section is populated based on real-world use of the pattern: task context, what worked, what required adjustment, and final conclusions.
