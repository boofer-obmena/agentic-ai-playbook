---
id: PATTERN-014
title: "Reflexive Recovery with Plan Revision"
title_ru: "Паттерн 14. «Рефлексивный цикл восстановления с пересмотром плана» (Reflexive Recovery with Plan Revision)"
type: pattern
subtype: functional
status: raw
source: "author's development"
date_added: 2026-05-07
version: 1.0
---

# Reflexive Recovery with Plan Revision

> **Паттерн 14. «Рефлексивный цикл восстановления с пересмотром плана» (Reflexive Recovery with Plan Revision)**

**Problem:** A standard Retry mechanism repeats the same plan without modification when an error occurs. If the error is caused by a fundamental change in the environment — an API change, a UI update — re-executing the same plan predictably yields the same result.

**Solution:** When an unhandled error occurs, the Reflexive Recovery Loop is activated. The agent enters analysis mode: (1) analyze the error trace and logs; (2) formulate a hypothesis about the root cause; (3) generate a revised plan; (4) validate the new plan; (5) submit it to the Orchestrator for acceptance and execution. The loop escalates the problem to a human if it cannot independently formulate a workable hypothesis.

**Experimental Verification:** Required. Deliberately introduce an API change that breaks the agent's plan. Verify that the Reflexive Recovery Loop generates a revised plan that adapts to the change, rather than blindly retrying the original.

**Application History:** Not applied. This section is populated based on real-world use of the pattern: task context, what worked, what required adjustment, and final conclusions.
