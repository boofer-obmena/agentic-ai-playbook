---
id: PATTERN-049
title: "Cross-Domain Cognitive Borrowing"
title_ru: "Кросс-доменное заимствование мышления"
type: pattern
subtype: functional
status: raw
source: "Master All 20 Agentic AI Design Patterns (SOURCE-006); author's development"
date_added: 2026-05-07
date_updated: 2026-05-11
version: 2.0
related: ["PATTERN-021", "PATTERN-017", "PATTERN-043", "PATTERN-044", "PATTERN-045", "PATTERN-011", "METHOD-015"]
---

# Cross-Domain Cognitive Borrowing

> **Кросс-доменное заимствование мышления**

**Problem:** An agent confined within the boundaries of its own knowledge domain and its own cognitive model can hit an impasse: the problem resists full formulation, a solution refuses to emerge, and the known patterns of its own domain offer no way forward. Yet the problem is not sufficiently articulated to bring it to Debate (PATTERN-021) — there is no clear question that different roles could meaningfully answer. The agent gets stuck in a state of unformedness.

**Solution:** The agent is given the architectural capability to temporarily step outside its domain into adjacent knowledge domains — not for ready-made answers, but for someone else's way of thinking. Every role (lawyer, financier, engineer) operates not only with its own set of facts but with its own cognitive algorithm: a way of decomposing problems, categories of analysis, typical reasoning patterns. The agent borrows these algorithms to view its unformed problem through an alien lens — and through this lateral transfer, finds a formulation or an insight that was inaccessible from within its own domain.

---

**Three initiation mechanisms (in order of decreasing realism):**

**Level 1 — Human (HITL).** A human operator, upon receiving the agent's result via PATTERN-044 (HITL) and finding it insufficiently deep, explicitly directs the agent into one or more adjacent domains for additional insight. This is the most reliable mechanism: the human possesses the meta-cognitive ability to assess that the agent lacks depth and to identify which adjacent domain might yield a productive lateral transfer.

**Level 2 — Orchestrator.** The Orchestrator (PATTERN-011) or a senior coordinator agent, upon receiving the executing agent's result, evaluates its depth against predefined criteria (confidence score, presence of unfilled sections in the artifact, an explicit "unable to formulate" signal from the executor). If depth is insufficient, the Orchestrator commands: "Go to domain X, view the problem through its categories." Unlike the human, the Orchestrator evaluates not content but formal signs of result insufficiency.

**Level 3 — Agent self-initiation (experimental mode).** The agent independently recognizes that a solution cannot be found within its domain — and initiates borrowing. Theoretically possible with high cognitive capabilities of the model (extended thinking modes, multi-step reasoning) and with an explicit architectural requirement: after exhausting N reflection cycles (PATTERN-043) without progress — attempt cross-domain search. However, this mechanism is unverified: LLMs tend to fit results to expectations rather than recognizing a cognitive dead end. The meta-cognitive ability of "I don't know" has not been confirmed for the current generation of models. Retained in the pattern as a discussion item — requires experimental verification as model cognitive capabilities improve.

---

**Two architectural requirements:**

(1) Access to other roles' knowledge bases that include descriptions of their cognitive models: not only "what a lawyer knows" but also "how a lawyer thinks" — their categories, their reasoning patterns, their evaluation criteria. This requires that each agent's semantic memory (PATTERN-045) include not only domain facts but also a meta-description of the role's cognitive model.

(2) Lateral transfer: the agent reinterprets the borrowed thinking pattern in its own categories — not mechanically transplanting it but reworking it to fit its own task. This is the key intellectual step of the pattern: not "the lawyer said approval is a commitment, therefore I will copy the legal schema," but "the lawyer sees approval as a chain of commitments; can I model my approval as a chain of acceptances in the terms of my own domain?"

---

**Output artifact — three components:**

- **Pre-borrowing result:** what the agent was able to produce operating solely within its own knowledge domain — the starting point from which it hit the impasse.
- **Post-borrowing result:** the reformulated problem or new hypothesis obtained through lateral transfer.
- **Transformation justification:** which domain the thinking pattern was borrowed from, what specific insight was gained, and how it changed the result.

This artifact structure allows the receiving party (Debate or human) to evaluate not only the final conclusion but also the correctness of the lateral transfer itself — "did you correctly apply legal thinking to a methodological problem?"

---

**Distinction from PATTERN-021 (Agent Debate).** Debate answers a formulated question through multiple-role contrast. Cross-Domain Borrowing occurs at the prior stage — when the question has not yet been formulated, when the agent is searching not for an answer but for the very possibility of asking a question. Debate is "what do you think about X?" Borrowing is "I don't know what to call X; let me look at the world through your categories, and perhaps I will see X."

**Distinction from PATTERN-017 (Dynamic Ontology).** PATTERN-017 describes the mechanism of discovering new connections within one's own domain through the periphery of assumptions. Cross-Domain Borrowing is an exit outward — into another domain, for another way of thinking.

**Distinction from METHOD-015 (Guided Exploration of Unknown Unknowns).** METHOD-015 remains within its own domain and systematically searches for blind spots — charting the edges of its own knowledge. PATTERN-049 temporarily exits into another domain for an alternative mode of thinking. They are complementary: METHOD-015, at the Gap Probing step, can use PATTERN-049 as a tool for probing a discovered gap; PATTERN-049 can use METHOD-015 for preliminary mapping — to understand which adjacent domain it makes sense to enter.

---

**Example:** A methodologist is designing an information system architecture and gets stuck: they cannot formulate how the document approval mechanism should work. In their methodological base — process patterns, state transitions, role models — there is no direct solution. They have exhausted cognitive reflection (PATTERN-043) within their domain — the result remains superficial. The human architect, via PATTERN-044, directs the agent: "Look at how a lawyer thinks about approval — not what norms they apply, but what categories they operate with."

The agent accesses the semantic memory of the legal role (PATTERN-045) and discovers: a lawyer thinks about approval not as a process but as a chain of commitments — each approver assumes responsibility. This is not a workflow but a sequence of acceptances.

Lateral transfer: the methodologist reinterprets the legal way of thinking in their own categories. Insight: "Approval can be modeled not as a workflow with state transitions but as a chain of accepted commitments, where each acceptance is not merely the fact of signing but a legally meaningful action with measurable consequences."

Output artifact: (1) original formulation — "the workflow model does not fit approval"; (2) new hypothesis — "the chain-of-accepted-commitments model"; (3) justification — the legal way of thinking about approval, reinterpreted in methodological terms.

With this artifact, the methodologist enters Debate (PATTERN-021): other roles can challenge both the hypothesis itself and the correctness of the lateral transfer — "are you sure the legal model of commitments is applicable to methodological design?"

**Related Entities:**

- Precedes [PATTERN-021](../PATTERN-021-agent-debate/) — helps formulate a problem that is then brought to role contrast
- Complements [PATTERN-017](../PATTERN-017-dynamic-ontology/) — PATTERN-017 explores its own domain; PATTERN-049 exits into others
- Can be initiated from [PATTERN-043](../PATTERN-043-single-role-reflective-deepening/) — when cognitive reflection within the domain is exhausted
- Can be initiated by a human via [PATTERN-044](../PATTERN-044-evolving-human-agent-trust/)
- Can be initiated by the Orchestrator via [PATTERN-011](../PATTERN-011-orchestrator/)
- Uses [PATTERN-045](../PATTERN-045-four-level-agent-memory/) — requires access to the semantic memory of other agents, including descriptions of their cognitive models
- Complements [METHOD-015](../METHOD-015-guided-exploration/) — METHOD-015 finds the gap; PATTERN-049 can be used to probe it

**Experimental Verification:** Required. Plan: give a methodologist agent a task for which no direct solution exists in its domain. Compare three modes: (a) with its own knowledge base only, (b) with access to adjacent-role knowledge bases and their cognitive model descriptions (Orchestrator-initiated), (c) with instructions for self-initiation after exhausting N reflection cycles. Measure: time to problem formulation, quality of the final solution, proportion of false self-initiations in mode (c).

**Application History:** Not applied. Status: raw.
