---
id: PRINCIPLE-007
title: "Iteration Limit as Safeguard"
title_ru: "Лимит итераций как предохранитель"
type: principle
status: raw
source: "author's development"
date_added: 2026-05-07
version: 1.0-preview
related: []
---

# Iteration Limit as Safeguard

> **Лимит итераций как предохранитель**

An agent without a hard limit on the number of iterations is a systemic risk. A hard iteration limit is not a restriction on the agent's autonomy — it is its prerequisite. When designing any agent loop, the first step is to define the maximum number of iterations and the agent's behavior when the limit is reached: stop, escalate, or log.
