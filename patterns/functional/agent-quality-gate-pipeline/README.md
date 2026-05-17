---
id: PATTERN-051
title: "Agent Quality Gate Pipeline"
title_ru: "Контроль качества в жизненном цикле агента"
type: pattern
subtype: engineering
status: raw
source: "Master All 20 Agentic AI Design Patterns (SOURCE-006); author's development"
date_added: 2026-05-07
version: 1.0
related: ["PATTERN-002", "PATTERN-043", "PATTERN-044", "PATTERN-020", "PATTERN-030"]
---

# Agent Quality Gate Pipeline

> **Контроль качества в жизненном цикле агента**

**Problem:** Agent evaluation is typically reduced to two measures: the human's subjective assessment ("looks good / doesn't look good") and the final accuracy of the result if it can be measured objectively. This is insufficient for production agent systems. The human cannot evaluate every output of every agent — this does not scale. Subjective assessment is inconsistent — the same human rates the same output differently depending on time of day and fatigue. And the lack of intermediate quality gates means that a degradation in agent performance is detected only after the result has already been delivered — post-mortem, not proactively.

**Solution:** An external quality evaluation circuit is introduced into the agent system architecture — a pipeline of automated quality gates that operate independently of the agent being evaluated and provide a quantitative, reproducible quality signal at multiple stages of the agent's lifecycle.

Golden Set Regression. A curated set of input-output pairs is maintained — tasks for which the correct answer is known with high confidence. After every agent update (model change, prompt change, rule change via PATTERN-020), the agent runs through the Golden Set. Regression is detected if the agent's accuracy on the Golden Set drops below a threshold. This is a smoke test: not "how good is the agent?" but "has the agent gotten worse than its previous version?"

LLM-as-Judge. For tasks where the correct answer cannot be determined algorithmically, a separate Judge agent evaluates the executing agent's output against a rubric. The Judge is not the same agent with a different prompt — it is an architecturally separate component with its own evaluation rubric, its own context, and no access to the executing agent's generation context. The Judge returns a structured verdict: (a) overall quality score (0–1), (b) per-criterion breakdown (completeness, accuracy, relevance, consistency), (c) specific issues found with artifact references. The Judge's rubric is the primary configuration artifact of the quality gate — it defines what "good" means for each agent type.

Quality gate placement. Quality gates are positioned at three points in the agent's lifecycle: (1) Pre-delivery gate — the agent's output passes through the Judge before reaching the human; if the score is below the threshold, the output goes to internal revision (PATTERN-043) rather than to the human. (2) Post-update gate — Golden Set Regression after every agent update; a drop below the threshold blocks the update from reaching production. (3) Periodic audit gate — a scheduled full pass of the agent through an extended evaluation set; detects slow degradation (model drift) that individual pre-delivery gates might miss.

Quality gates are not quality guarantees. They are automated signals for human attention. A pre-delivery gate does not replace the human — it filters out outputs that are unambiguously below the quality bar, so the human only reviews outputs where the quality signal is ambiguous or high.

Quality signal feedback loop. Judge verdicts accumulate over time. The Ratchet Loop (PATTERN-020) uses them to identify systemic weaknesses: if the Judge consistently flags "incompleteness" for a given agent type, this becomes a candidate for a rule change or prompt refinement. Active learning (PATTERN-030) uses Judge-flagged outputs as candidates for human correction — the worst-rated outputs are the highest-signal training examples.

**Example:** An analyst agent generates a contract. Before the contract reaches the client, the pre-delivery gate activates: the Judge agent evaluates the contract against a rubric — completeness (all required clauses present?), accuracy (are the legal references correct?), consistency (no contradictory clauses?). The Judge returns a score of 0.72 — below the pre-delivery threshold of 0.85. The quality gate routes the contract back to the agent with the Judge's specific issues: "clause 4.2 contradicts clause 3.1 in liability language; missing force majeure section." The agent performs internal reflection (PATTERN-043) and revises the contract. Second pass: 0.91 — delivered to the human. The human sees a pre-vetted contract, reviews only the flagged sections, and approves.

A week later, the agent is updated with a new prompt. The post-update gate runs Golden Set Regression: accuracy drops from 0.88 to 0.81 — regression detected. The update is blocked. The team investigates: the new prompt inadvertently changed the agent's behavior on a specific contract type. The prompt is fixed, Golden Set passes — the update is cleared.

**Related Entities:**

- [PATTERN-002](../PATTERN-002-agent-auditor/): the Judge is a specialized instance of the Agent-Auditor — evaluating not architecture but output quality
- [PATTERN-043](../PATTERN-043-single-role-reflective-deepening/): triggered by the pre-delivery gate when the quality score is below threshold — the agent revises the output before it reaches the human
- [PATTERN-044](../PATTERN-044-evolving-human-agent-trust/): quality gates reduce the number of HITL checkpoints by filtering out outputs that are unambiguously below the bar
- [PATTERN-020](../PATTERN-020-ratchet-loop/): aggregate Judge verdicts feed into the Ratchet Loop as a signal for systemic behavior improvements
- [PATTERN-030](../PATTERN-030-active-learning-via-artifact-correction/): Judge-flagged outputs are the highest-signal training examples for active learning

**Experimental Verification:** Required. Test plan: deploy an agent with and without quality gates. Measure: (1) human review time per output with and without pre-delivery gates, (2) frequency of Golden Set regressions caught before reaching production, (3) correlation between Judge scores and human quality ratings — to calibrate the rubric.

**Application History:** Not applied. Status: raw.
