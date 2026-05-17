---
id: BACKLOG-011
title: "Upstream Loop: From Vague Goal to Measurable KPIs (Communicator → Task Formulator)"
title_ru: "Upstream-контур: от размытой цели к измеримым KPI (Коммуникатор → Постановщик задач)"
type: backlog
status: Idea
subtype: "upstream loop"
source: "Master All 20 Agentic AI Design Patterns (SOURCE-006); author's development"
date_added: 2026-05-07
version: 1.0
related: ["PATTERN-022", "PATTERN-047"]
---

# Upstream Loop: From Vague Goal to Measurable KPIs (Communicator → Task Formulator)

> **Upstream-контур: от размытой цели к измеримым KPI (Коммуникатор → Постановщик задач)**

A user formulates a task vaguely: "improve documentation quality." An executor agent cannot work with a vague goal — it needs measurable KPIs. An upstream loop is required: Communicator (gathers the full picture through targeted questions) → Task Formulator agent (specifies measurable KPIs) → alignment with the user through the Communicator → handoff to the executor. Without this loop, PATTERN-047 (Target Monitoring) cannot be applied.

**Boundary with PATTERN-022 (Proactive Goal Interpreter):** PATTERN-022 is about the agent not waiting for commands but seeking opportunities. The Upstream Loop is about a vague goal passing through a formalization stage before becoming a task.

Requires dedicated elaboration in an arch-mining session.
