---
id: PATTERN-045
title: "Unified Agent Memory Model: Four Cognitive Levels"
title_ru: "Единая модель памяти агента: четыре когнитивных уровня"
type: pattern
subtype: functional
status: raw
source: "Master All 20 Agentic AI Design Patterns (SOURCE-006); author's development"
date_added: 2026-05-07
version: 1.0
related: ["PATTERN-043", "PATTERN-020", "PATTERN-025", "PATTERN-044", "PHILOSOPHY-006"]
---

# Unified Agent Memory Model: Four Cognitive Levels

> **Единая модель памяти агента: четыре когнитивных уровня**

**Problem:** Standard agent memory models operate on two or three levels (short-term, episodic/semantic, long-term). This is insufficient for an agent that must not only accumulate facts but also extract its own behavior rules from accumulated experience. The classic three-level architecture creates a conceptual gap between raw memory storage and the agent's ability to draw conclusions from its own history: facts accumulate, but the agent does not become smarter from them — its rules remain whatever the architect wrote at the design stage.

**Solution:** A unified four-level memory model is introduced — one that does not treat memory as separate disconnected stores but as a single cognitive pipeline: from a pressure-saturated short-term buffer to a behavioral level where the agent independently derives patterns of effective action.

Level 1 — Short-term memory. An active window of limited capacity (token budget). Holds the current state of the dialog, the immediate task context, and the last N steps of the execution trace. Operational pressure is high: new inflows constantly displace old entries. The agent must decide what rises to Level 2. The short-term buffer is the only source of memory the model has direct causal access to during generation.

Level 2 — Episodic/semantic memory. Structured, searchable storage. Records of completed tasks with their results, extracted facts, domain knowledge. The primary source for Retrieval-Augmented Generation (RAG). This is where factual experience accumulates: "did X, got Y under conditions Z."

Level 3 — Long-term memory. Compact, compressed representations: mental models, persistent beliefs about the world, entity relationship maps. Analogous to expert intuition — not an exhaustive log, but key invariants derived from the entire history of observations.

Level 4 — Procedural memory (author's addition to the standard three-level model). The agent's own behavior rules, derived from its own experience rather than written by the architect. The Ratchet Loop (PATTERN-020) is the mechanism that lifts effective strategies from Levels 1 and 2 to Level 4: a set of patterns of successful behavior that the agent has accumulated and verified. Critically, procedural memory is not the architect's prompt — it is the agent's own rules of operation, distilled from its history.

The four levels form a pipeline: operational pressure at Level 1 forces decisions about what deserves to be retained at Level 2; a critical mass of episodes at Level 2 enables the extraction of invariants at Level 3; and verified behavioral patterns at Levels 2 and 3 become candidates for procedural rules at Level 4 through the Ratchet Loop.

Memory is not a single store but a dynamic system with different access speeds, different lifetimes, and a mechanism for elevating content from lower cognitive levels to higher ones. This is an architectural requirement: the agent's cognitive architecture must explicitly define how content flows between levels.

**Example:** An analyst agent processes a series of client requests. Level 1: the current dialog — the client asks to prepare a contract for a company engaged in both services and the sale of equipment. The agent drafts a mixed contract. Level 2 (after task completion): records — "mixed contract for dual-type company, used templates A and B, the client requested 3 revisions." Level 3: after 20 clients, the agent forms a mental model — "sole proprietors consistently request simpler terms than LLCs." Level 4: the Ratchet Loop converts this model into a procedural rule — "when the client is a sole proprietor, start with the minimum version of the contract, adding clauses only as needed."

Without Level 4, the agent would know from Level 3 that sole proprietors prefer simplicity but would never start a new dialog with the simplified template — the architect did not program this behavior. With Level 4, the agent generates the rule itself and begins applying it.

**Related Entities:**

- [PATTERN-043](../PATTERN-043-single-role-reflective-deepening/) loads relevant facts from Level 2 and Level 3 into Level 1 during the reflection phase
- [PATTERN-020](../PATTERN-020-ratchet-loop/) is the primary mechanism populating Level 4: it lifts effective behavioral strategies to procedural memory
- Fragments of Level 2 can be externalized into [PATTERN-025](../PATTERN-025-three-level-rule-architecture/) Level 2 (operational rules) and Level 1 (global constraints)
- Training pairs from [PATTERN-044](../PATTERN-044-evolving-human-agent-trust/) HITL checkpoints feed into Level 2 as high-signal episodes
- Derives from [PHILOSOPHY-006](../PHILOSOPHY-006-primacy-of-iterative-self-deepening/): the pipeline architecture of memory is what enables iterative self-deepening

**Experimental Verification:** Required. Test plan: deploy two versions of an agent — with three-level and four-level memory — on identical tasks. Measure: (1) proportion of behavioral improvements attributable to the agent's own rules vs. architect-written rules over time, (2) quality of derived Level 4 rules (expert evaluation), (3) frequency of overgeneralization from Level 3 to Level 4.

**Application History:** Not applied. Status: raw.
