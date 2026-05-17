---
id: PATTERN-048
title: "Dynamic Task Queue Prioritizer"
title_ru: "Динамический приоритизатор очереди задач"
type: pattern
subtype: functional
status: raw
source: "Master All 20 Agentic AI Design Patterns (SOURCE-006); author's development"
date_added: 2026-05-07
version: 1.0
related: ["PATTERN-006", "PATTERN-011", "PATTERN-025"]
---

# Dynamic Task Queue Prioritizer

> **Динамический приоритизатор очереди задач**

**Problem:** Agent task prioritization is typically designed as a static rule — a fixed weight formula evaluated once when the task is created. This ignores the reality that priority is a dynamic function of time and changing external conditions. A task created with low priority can become critical after two hours — but the static formula does not account for this. A task with high initial priority may have lost urgency because its prerequisite changed — but the formula does not know this. As a result, the agent processes tasks in an order that does not reflect the system's current needs.

**Solution:** Task prioritization is extracted into a separate architectural component — a Prioritizer — that continuously recalculates priorities based on a multi-dimensional function incorporating both static and dynamic parameters.

Priority function. Priority is not a scalar constant but the output of a function: P(task, time, context). Parameters: (1) static criticality — assigned at creation, does not change (is this a client-facing task or an internal maintenance task?), (2) age — time since creation, with a configurable penalty (a low-priority task should not wait indefinitely), (3) dependency state — has a prerequisite task been completed? has a new dependency emerged? (4) external trigger — has an event occurred that changes the task's urgency? (a human escalation via HITL, a drift alert from the monitoring system), (5) "window pressure" — how close is the task's deadline or the end of the agent's operational window?

Decay function. Low-priority tasks accumulate a configurable "age penalty" to prevent starvation: priority grows with idle time. High-priority tasks do not accumulate a penalty — they are already at the top of the queue.

Re-evaluation trigger. The prioritizer re-evaluates the queue not on a timer but on events: arrival of a new task, completion of a task, external escalation (from HITL or monitoring), human override signal.

Re-prioritization budget. To prevent thrashing — where a task is constantly preempted — the prioritizer respects a minimum quantum: a task that has begun execution cannot be preempted before consuming a configurable minimum of resources (token budget or wall time). The human can override this limit via HITL.

Configuration, not code. The prioritizer's weight coefficients live in the operational rules layer (PATTERN-025 Level 2) and can be tuned without changing the system architecture.

**Example:** A legal agent has three tasks in flight: (1) high-priority — an urgent amendment to a contract to be signed today, (2) medium-priority — a standard NDA, (3) low-priority — updating the template library. At 10:00, task (1) is active. At 10:30, task (2) arrives — placed in the queue. At 10:45, the client escalates task (2) — "the counterparty is waiting for the NDA now." The prioritizer receives a signal via HITL, recalculates: task (2) priority exceeds task (1) — the agent pauses task (1) after completing the current section — honoring the minimum quantum — and begins task (2). At 11:15, the monitoring system fires a drift alert on task (2) — the agent is writing an overly restrictive NDA. The prioritizer receives the alert, raises the signal priority — the orchestrator forces a context reset and re-inspection of task (2) with a corrected specification. At 12:00, task (2) is completed. The agent returns to task (1).

Without a dynamic prioritizer, all three tasks would have been processed in the order of creation — the client's urgent need and the monitoring alert would have been ignored.

**Related Entities:**

- [PATTERN-006](../PATTERN-006-planning-and-task-decomposition/): planning creates the queue; the prioritizer determines the execution order within the queue
- [PATTERN-011](../PATTERN-011-orchestrator/): the Orchestrator uses the Prioritizer to select the next task, respecting minimum quantum and human override
- [PATTERN-025](../PATTERN-025-three-level-rule-architecture/): prioritizer coefficients are stored at Level 2 (operational rules), changeable without rebuilding the system
- [PATTERN-044](../PATTERN-044-evolving-human-agent-trust/): HITL escalation signals feed into the prioritizer as external priority triggers
- [PATTERN-047](../PATTERN-047-targeted-monitoring-drift-detection/): monitoring alerts feed into the prioritizer as external priority triggers

**Experimental Verification:** Required. Test plan: deploy a system with static and dynamic prioritization on identical task flows. Measure: (1) average and maximum wait time for high-criticality tasks, (2) number of starvation events (low-priority tasks delayed beyond the starvation threshold), (3) number of preemption events.

**Application History:** Not applied. Status: raw.
