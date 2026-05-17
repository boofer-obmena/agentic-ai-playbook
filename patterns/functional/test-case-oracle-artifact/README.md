---
id: PATTERN-007
title: "Test Case as Oracle Artifact"
title_ru: "Паттерн 7. «Тест-кейс как артефакт со встроенным оракулом» (Test Case as Oracle Artifact)"
type: pattern
subtype: functional
status: raw
source: "author's development"
date_added: 2026-05-07
version: 1.0
---

# Test Case as Oracle Artifact

> **Паттерн 7. «Тест-кейс как артефакт со встроенным оракулом» (Test Case as Oracle Artifact)**

**Problem:** Subjective evaluation of test results breeds disputes and does not ensure reproducibility. If the acceptance criterion is framed vaguely, two different agents can render opposite verdicts for the same result.

**Solution:** A test case is a full-fledged pipeline artifact with a strict structure: Identifier → Linked Requirement (reference to FR) → Preconditions → Action Sequence → Expected Result (precisely formulated, verifiable). The verdict is always binary: Passed / Not Passed. Intermediate states are not permitted.

**Example:** An FR contains the requirement: "When creating an order with an item quantity exceeding 1,000 units, the system must request confirmation from the manager." A QA agent creates a test case: Precondition — an authenticated user with the "Manager" role. Action — add an item with a quantity of 1,001 units. Expected Result — a confirmation dialog appears with the exact text.

**Experimental Verification:** Hand the QA agent a deliberately broken version of the feature and a correct version with different dialog text. Verify: both versions receive a "Not Passed" verdict with different, precise diagnoses.

**Application History:** Not applied. This section is populated based on real-world use of the pattern: task context, what worked, what required adjustment, and final conclusions.
