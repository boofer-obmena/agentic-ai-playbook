---
id: PATTERN-023
title: "Multi-Variant Plan Generator"
title_ru: "Паттерн 23. «Многовариантный генератор плана» (Multi-Variant Plan Generator)"
type: pattern
subtype: functional
status: raw
source: "Master All 20 Agentic AI Design Patterns (SOURCE-006); author's development"
date_added: 2026-05-07
version: 1.0
related: []
---

# Multi-Variant Plan Generator

> **Паттерн 23. «Многовариантный генератор плана» (Multi-Variant Plan Generator)**

**Problem:** When presented with a complex task, an agent generates a single plan and immediately proceeds to execute it. If the plan turns out to be suboptimal or non-viable, this only becomes apparent during execution — after significant resources have already been spent. Alternative approaches are never considered.

**Solution:** Before beginning execution, the agent generates N independent plan variants (typically 3–5). Each variant is evaluated against a set of criteria: speed to result, required resources, resilience to failure, and compliance with constraints. The Orchestrator or human architect selects the optimal variant for execution. The remaining variants are preserved as "fallback routes" — ready to be activated if the primary plan fails.

**Example:** Task: migrate a database with zero data loss and minimal downtime. Variant A: blue-green deployment (zero downtime, high complexity, requires double the resources). Variant B: migration during a maintenance window (2-hour downtime, low complexity, minimal resources). Variant C: gradual migration via replication (minimal risk, long duration). The architect selects variant B as optimal given the current constraints.

### Extension: Spawn-Restrict-Collect

Once a route is selected, the master Orchestrator agent does not execute everything sequentially itself. Instead:

**Spawn** — spawns sub-agents for parallel execution of independent sub-tasks. Each sub-agent receives an isolated session with a clean context.

**Restrict** — each sub-agent is issued a deliberately reduced tool set scoped to its specific sub-task. An agent analyzing documentation has no physical access to file-editing tools.

**Collect** — the Orchestrator gathers sub-agent results, integrates them into the overall solution architecture, and "completes the contract" with each sub-agent.

Key properties: parallelism (execution time is determined by the longest task, not the sum of all); context isolation; least privilege (a sub-agent cannot cause harm outside its perimeter).

**Experimental Verification:** Required. Present the agent with a task that has two fundamentally different solution approaches. Verify: the agent generates both variants, explicitly describes the trade-offs of each, and does not begin execution until it receives a selection from the Orchestrator or human architect.

**Application History:** Not applied. This section is populated based on real-world use of the pattern: task context, what worked, what required adjustment, and final conclusions.
