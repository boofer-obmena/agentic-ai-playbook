---
id: PATTERN-021
title: "Agent Debate"
title_ru: "Паттерн 21. «Дебаты агентов» (Agent Debate)"
type: pattern
subtype: functional
status: raw
source: "author's development"
date_added: 2026-05-07
version: 1.0
---

# Agent Debate

> **Паттерн 21. «Дебаты агентов» (Agent Debate)**

**Problem:** A single agent analyzing a complex task is prone to confirmation bias: it reinforces its initial hypothesis while ignoring or smoothing over contradictory signals. This is especially dangerous in architectural decisions, where a mistaken choice has long-term consequences.

**Solution:** Two or more agent instances receive the same input data but different roles: one argues "for," the other "against" the proposed solution. The Orchestrator relays the agents' positions to each other in turn (N rounds). A synthesizer-agent analyzes the final exchange and formulates a weighted conclusion. Key property: the agents are unaware of the opponent's existence before the debate begins — they formulate their positions independently.

**Example:** A data storage architecture must be chosen: relational DB vs. document-oriented DB. Agent A argues for relational: transactional guarantees, strict schema, mature ecosystem. Agent B argues for document-oriented: schema flexibility, horizontal scaling, development speed. After three rounds, the synthesizer-agent formulates a recommendation with explicit trade-offs for each option.

### Application Context: Jagged Intelligence

Agent debate is especially valuable under conditions of "Jagged Intelligence" — the phenomenon where an agent demonstrates exceptional performance on some tasks and unexpected failures on adjacent ones. Uniform competence cannot be assumed: a model may brilliantly analyze technical code while making gross errors in planning logic. When designing debates, select agents whose competence "jags" lie in different areas — so that the strengths of one compensate for the weaknesses of the other.

**Experimental Verification:** Take a task with a known correct answer that contradicts the intuitive one. Run a single agent (control) and two agents in debate mode. Compare the quality of the final decision. Expected result: debate mode more frequently leads to the correct answer, by surfacing weaknesses in the initial position.

**Application History:** Not applied. This section is populated based on real-world use of the pattern: task context, what worked, what required adjustment, and final conclusions.
