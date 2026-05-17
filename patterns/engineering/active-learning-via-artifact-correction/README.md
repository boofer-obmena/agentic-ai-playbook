---
id: PATTERN-030
title: "Active Learning via Artifact Correction"
title_ru: "Паттерн 030. «Активное обучение через коррекцию артефакта» (Active Learning via Artifact Correction)"
type: pattern
subtype: engineering
status: raw
source: "Master All 20 Agentic AI Design Patterns (SOURCE-006); author's development"
date_added: 2026-05-07
version: 1.0
related: ["PATTERN-020"]
---

# Active Learning via Artifact Correction

> **Паттерн 030. «Активное обучение через коррекцию артефакта» (Active Learning via Artifact Correction)**

**Problem:** Static prompts do not adapt to the specifics of a particular organization, the style of its documents, or the preferences of individual users. A system that works correctly "on average" can systematically produce results that require manual rework in a specific context.

**Solution:** Every manual correction of an artifact made by a human is automatically converted into a training pair: "Agent's original version → Human's corrected version." This pair is added to the vector database as a few-shot example for future similar queries. The learning loop operates exclusively on the ground-truth facts layer: the human corrects a fact, the system rebuilds the projection. Corrections of suboptimal plans (see Pattern 20) are captured separately: they create "Suboptimal Plan → Preferred Plan" pairs. After accumulating a sufficient number of training pairs, the agent begins reproducing the preferred style without manual intervention.

**Example:** An analyst agent produces functional requirements in an academic style. A methodologist corrects several items, rephrasing them in the organization's more operational style. The system captures three training pairs. On the fourth request, the agent independently uses the operational style. By the tenth, it fully reproduces the corporate template.

**Experimental Verification:** Required. Simulate 3 cycles of "request → agent output → manual correction." Record each correction as a training pair. On the 4th request of a similar type, the agent should independently apply the learned style without additional instructions.

**Application History:** Not applied. This section is populated based on real-world use of the pattern: task context, what worked, what required adjustment, and final conclusions.
