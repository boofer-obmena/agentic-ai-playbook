---
id: PATTERN-006
title: "Smart Dispatcher"
title_ru: "Паттерн 6. «Фильтр-подбор (Умный диспетчер)» (Smart Dispatcher)"
type: pattern
subtype: functional
status: raw
source: "author's development"
date_added: 2026-05-07
version: 1.0
---

# Smart Dispatcher

> **Паттерн 6. «Фильтр-подбор (Умный диспетчер)» (Smart Dispatcher)**

**Problem:** Manual assignment of tasks to executors is a bottleneck in any pipeline. Agents differ in competencies, current workload, and specialization. Without automated dispatching, tasks are distributed inefficiently.

**Solution:** The dispatch function selects the optimal executor agent based on two groups of filters. Static filters: competency matrix (which types of tasks the agent can handle), specialization. Dynamic filters: current workload, online status. When conditions are equal, the least-loaded criterion is applied.

**Example:** A system has three developer agents. The first specializes in accounting modules, the second in integrations, the third is a generalist but is occupied with two tasks. An integration development task arrives. The Dispatcher selects the second agent as optimal by specialization.

**Experimental Verification:** Create a virtual pool of 3 agents with different competency matrices. Form a queue of 5 tasks of different types. Verify: each task is assigned to the agent that is optimal specifically for it.

**Application History:** Not applied. This section is populated based on real-world use of the pattern: task context, what worked, what required adjustment, and final conclusions.

### Extension: Dispatcher-by-Goal (Analog Dispatcher)

The Dispatcher does not refuse — it looks for an analog. The basic dispatcher logic is to route a request to a resource. The extended logic is to route to a goal. If the requested resource is unavailable (no license, no access, policy-restricted), the dispatcher identifies the core objective of the task and proposes an approved analog. Refusal is the last step, not the first.

**Algorithm:** (1) receive the request → (2) check resource availability → (3) if unavailable — identify the core objective of the task → (4) find an analog in the approved list → (5) propose the analog → (6) only if no analog is found — escalate or refuse with an explanation.
