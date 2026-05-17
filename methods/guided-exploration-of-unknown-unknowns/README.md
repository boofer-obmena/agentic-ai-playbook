---
id: METHOD-015
title: "Guided Exploration of Unknown Unknowns"
title_ru: "Управляемое исследование неизвестного незнания (Guided Exploration of Unknown Unknowns)"
type: method
status: raw
subtype: "method / technique"
source: "Master All 20 Agentic AI Design Patterns (SOURCE-006); author's development"
date_added: 2026-05-11
version: 1.0
related: ["PATTERN-002 (primary consumer)", "PATTERN-017 (complements)", "PATTERN-049 (complements)"]
---

# Guided Exploration of Unknown Unknowns

> **Управляемое исследование неизвестного незнания (Guided Exploration of Unknown Unknowns)**

**Problem:** After an initial domain analysis, an agent forms a picture based on what it knows and has been able to extract. But in ill-structured, high-stakes domains (system architecture, strategic planning, scientific analysis), the greatest risk lies not in what the agent knows imprecisely, but in what it does not know at all — the unknown unknowns. An agent confined within the boundaries of what it has discovered has no mechanism to systematically search for gaps in its own knowledge. The result: confident but incomplete analysis.

**Solution:** A five-step algorithm of guided divergence and convergence, transforming the agent from a query executor into an explorer.

---

**Step 1. Divergent Generation.** The agent generates N distinct ideas, hypotheses, or approaches on the topic (N ≥ 20), with explicit instructions to maximize variability. Technical implementation: high sampling temperature (0.8–1.0), an explicit prohibition on repetition, and a requirement to cover different angles and scales of consideration. The goal is not the quality of each individual idea but the breadth of coverage of the idea space.

**Step 2. Clustering.** The generated ideas are vectorized (embedding model) and clustered. The result is a topic map: dense clusters (areas where many ideas exist), sparse regions (areas with few ideas), and voids (areas with no ideas). This step translates the problem from "we don't know what we don't know" to "we can see where we have no ideas."

**Step 3. Gap Analysis.** The agent receives the cluster map and is tasked with answering: "Which topics are entirely absent?", "Which clusters are unexpectedly sparse?", "Which adjacent areas are untouched?", "Where is the blank spot between two dense clusters?" The agent formulates a list of gaps — areas of unknown unknowns, now expressed explicitly.

**Step 4. Gap Probing.** For each detected gap, the agent generates exploratory queries — not for a ready answer, but for exploratory intelligence. The queries are directed at: searching for relevant sources on the gap, formulating hypotheses about what might occupy the gap, and identifying adjacent domains that may hold relevant knowledge.

**Step 5. Synthesis.** The probing results are aggregated: a gap map annotated with "closed" (relevant knowledge found), "narrowing" (approaches to filling it have been discovered), and "open" (requires a human expert). The final artifact is not merely an answer to the original question, but a knowledge map with explicitly marked boundaries between the known and the unknown.

---

**Difference from PATTERN-049 (Cross-Domain Borrowing).** PATTERN-049 has an agent temporarily step into another domain to adopt the thinking style of a different role. METHOD-015 has the agent remain in its own domain but systematically search for blind spots within it. They are complementary: METHOD-015 discovers a gap; PATTERN-049 can be used at Step 4 (Gap Probing) to search for insight in an adjacent domain.

**Difference from PATTERN-017 (Dynamic Ontology).** PATTERN-017 discovers new connections between known concepts by examining the periphery of assumptions — this is intra-domain enrichment. METHOD-015 discovers the absence of concepts — this is domain boundary mapping.

**Example:** The Auditor agent (PATTERN-002) has completed an information system architecture audit. Standard analysis revealed: 3 performance issues, 2 security issues, 1 scalability issue. METHOD-015 is activated: divergent generation of 25 hypotheses about potential problems, clustering reveals a dense "performance" cluster, a sparse "fault tolerance" cluster, and a void at "regulatory compliance." Gap Analysis formulates a gap: "compliance with Federal Law No. 152-FZ on personal data not checked." Gap Probing searches for relevant regulatory documents. Synthesis adds a "Regulatory Risks" section to the audit with specific inspection items.

**Primary Consumer:** PATTERN-002 (Auditor Agent) — systematic architecture audit. Also applicable: PATTERN-006 (Planning) — before generating a plan in an unfamiliar domain; PATTERN-021 (Debate) — at the argument preparation stage, to detect overlooked perspectives.

**Experimental Verification:** Required. Plan: give an auditor agent an architecture analysis task with a deliberately introduced blind spot (an omitted domain). Compare two modes: (a) standard analysis, (b) standard analysis + METHOD-015. Measure: whether the blind spot is detected, number of false gaps, latency overhead.

**Application History:** Not applied. This section is populated based on real-world use of the method: task context, what worked, what required adjustment, and final conclusions.
