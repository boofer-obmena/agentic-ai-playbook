---
id: BACKLOG-008
title: "Spawn-Restrict-Collect"
title_ru: "Spawn-Restrict-Collect"
type: backlog
status: Hypothesis
source: ""
date_added:
version:
related: ["PATTERN-023"]
---

# Spawn-Restrict-Collect

> **Spawn-Restrict-Collect**

The Orchestrator does not execute subtasks sequentially. Instead: **Spawn** — spawns sub-agents for parallel execution; **Restrict** — gives each a reduced set of tools scoped to its task; **Collect** — gathers the results. Properties: parallelism, context isolation, least privilege. An extension of PATTERN-023.
