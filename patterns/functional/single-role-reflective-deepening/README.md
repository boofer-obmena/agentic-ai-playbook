---
id: PATTERN-043
title: "Single-Role Reflective Deepening"
title_ru: "Рефлексивное самоуглубление в рамках одной роли"
type: pattern
subtype: functional
status: raw
source: "Master All 20 Agentic AI Design Patterns (SOURCE-006); author's development"
date_added: 2026-05-07
version: 1.0
related: ["PHILOSOPHY-006", "PATTERN-021", "PATTERN-014", "PATTERN-020"]
---

# Single-Role Reflective Deepening

> **Рефлексивное самоуглубление в рамках одной роли**

**Problem:** An agent generating output in a single pass produces a "first draft" — material that has undergone no internal review for completeness, depth, or alignment with the original request. The model is susceptible to confirmation bias: it cannot see the weaknesses of its own generation because it remains inside the same reasoning context in which the material was produced.

**Solution:** The agent performs several iterations of work on the material while staying within a single role. After generating a draft, the agent deliberately disengages — it resets its generation memory. It then returns to the material "with fresh eyes," using a specialized Critic prompt that directs it to analyze: alignment with the request, completeness, depth, breadth of coverage, and presence of errors. If needed, the agent consults its knowledge base for supplementary information — including material not directly related to the topic that may yield an unexpected insight. The loop repeats until acceptable quality is reached.

A key architectural constraint: the agent does not change roles during reflection. The methodologist remains a methodologist, the engineer remains an engineer. The Critic is not a separate role but an operating mode of the same role with a reset context and a specialized prompt. Changing roles turns Reflection into Debate (PATTERN-021).

Reflection depth is parameterized through an architectural knob — the "level of task criticality": for operational tasks with low error cost, single-pass generation without reflection; for medium-criticality tasks, two to three verification iterations; for expert tasks with high error cost, iterations until the iteration limit is reached or quality convergence is achieved.

**Example:** A system architect (methodologist) receives a task to describe a target information system architecture. First iteration: the agent sketches out a structure — components, connections, data flows. Context reset. Second iteration: the agent returns to the draft in Critic mode, analyzing it for completeness (are all aspects covered?), internal consistency (are there contradictions?), and alignment with original requirements. It consults its knowledge base — finds a description of a similar architecture from an adjacent domain, spots a pattern it had missed. Third iteration: the agent refines the architecture incorporating the discovered pattern and the Critic's notes.

**Related Entities:**
- Derives from [PHILOSOPHY-006: Primacy of Iterative Self-Deepening](../../philosophy/PHILOSOPHY-006-iterative-self-deepening/)
- Alternative to [PATTERN-021: Agent Debate](../../patterns/functional/PATTERN-021-agent-debate/): Reflection is deepening within one role; Debate is contrast between different roles
- Complements [PATTERN-014: Reflective Recovery Loop](../../patterns/functional/PATTERN-014-reflective-recovery-loop/): PATTERN-014 triggers reactively upon error and rebuilds the plan; PATTERN-043 works proactively on quality before delivering the result
- Complements [PATTERN-020: Ratchet Loop](../../patterns/functional/PATTERN-020-ratchet-loop/): PATTERN-020 operates on a days/weeks horizon and improves agent rules; PATTERN-043 works here and now on a specific artifact

**Experimental Verification:** Required. Test plan: compare output quality with Reflection (2, 3, and 5 iterations) against single-pass generation on a set of tasks of varying criticality. Metrics: expert quality assessment, execution time, token cost. Determine the optimal number of iterations for each criticality level.

**Application History:** Not applied. Status: raw.

**Implementations:** [implementations/](implementations/)

**Case Studies:** [case-studies/](case-studies/)

**Experiments:** [experiments/](experiments/)
