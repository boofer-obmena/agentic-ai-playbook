---
id: PATTERN-029
title: "Append-Only Session Log"
title_ru: "Паттерн 29. «Журнал сессии в режиме только-добавления» (Append-Only Session Log)"
type: pattern
subtype: functional
status: raw
source: "Master All 20 Agentic AI Design Patterns (SOURCE-006); author's development"
date_added: 2026-05-07
version: 1.0
related: ["PATTERN-009", "PATTERN-027"]
---

# Append-Only Session Log

> **Паттерн 29. «Журнал сессии в режиме только-добавления» (Append-Only Session Log)**

**Problem:** A long-running autonomous agent accumulates valuable internal state: decision history, sub-agent results, analyzed data. A process crash, network disruption, or container restart destroys this state. Storing state in a database requires managing transactions and schemas, slowing every step of the agent.

**Solution:** All agent session state is continuously written to a file in append-only mode. Each event — a new model output, a tool invocation, a context compaction trigger, an error — is appended as a separate line to the end of the file. The file is never overwritten. On failure and restart, the agent reads the file line by line from the beginning, replays the event history, and recovers state up to the failure point in milliseconds. Log management is placed outside the agent's own logic — software failures of the agent do not corrupt already-written data.

**Related Entities:** Pattern 9 (Immutable States) — the append-only log is a practical implementation of the immutability principle. Pattern 27 (Semantic Context Compaction) — context compaction events are recorded in the log, enabling precise reconstruction of the agent's memory state at any point in time.

**Experimental Verification:** Required. Launch an agent on a long task. Midway through execution, forcibly terminate the process (kill -9). Restart the agent. Measure: state recovery time (target: under 1 second), recovery accuracy (agent resumes from the correct point, does not repeat already-completed steps).

**Application History:** Not applied. This section is populated based on real-world use of the pattern: task context, what worked, what required adjustment, and final conclusions.
