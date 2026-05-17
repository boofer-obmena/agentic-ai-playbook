---
id: PATTERN-047
title: "Targeted Monitoring with Drift Detection"
title_ru: "Целевой мониторинг с дрейф-детекцией"
type: pattern
subtype: functional
status: raw
source: "Master All 20 Agentic AI Design Patterns (SOURCE-006); author's development"
date_added: 2026-05-07
version: 1.0
related: ["PATTERN-002", "PATTERN-025", "PATTERN-014", "PATTERN-020"]
---

# Targeted Monitoring with Drift Detection

> **Целевой мониторинг с дрейф-детекцией**

**Problem:** Monitoring in agent systems is often designed as a generic observability layer: collect all available metrics, log everything, then attempt to find useful signals in an ocean of data. This "monitor everything" approach has two fatal flaws. First, it generates noise that drowns the signal — a human operator cannot track 200 metrics simultaneously. Second, it misses the most dangerous class of failures: gradual goal drift, where the agent continues to operate "correctly" in terms of individual actions but progressively deviates from the original objective — a phenomenon invisible to per-action monitoring but catastrophic in its cumulative effect.

**Solution:** Monitoring is designed not as a generic observability layer but as a targeted subsystem tied to the specific goals of each agent. Instead of "monitor everything," the architect selects a small set of goal-proximity metrics — indicators that directly measure the agent's movement toward or away from its stated objective.

Goal-proximity metrics. For each agent goal, 3–5 quantitative indicators are defined that correlate directly with goal achievement. These are not system-health metrics (CPU, memory, latency) but semantic alignment metrics: "how close is the current artifact to what was requested?", "what share of subtasks has been completed in the expected direction?", "is the agent exploring the expected solution space or drifting into an adjacent one?"

Drift detection. Monitoring tracks not absolute values but trend direction and rate of change over a moving window. A single outlier is a signal for inspection; a steady negative trend over N consecutive windows is a drift event. Drift detection is not about "did the agent make a mistake?" but "has the agent's trajectory changed direction?" — a higher-order signal.

Monitoring-as-a-service, not a monolithic dashboard. A specialized monitoring sub-agent receives goal-proximity metrics from executing agents, maintains a trend log, and fires escalation events: (1) "trend alert" — inspect but do not interrupt, (2) "drift warning" — notify the human via the HITL controller (PATTERN-044), (3) "critical divergence" — hard-stop the agent and trigger a recovery loop (PATTERN-014).

Three monitoring levels by rule tier. Level 1 (global constraints — PATTERN-025): mandatory baseline metrics for every agent — latency, error rate, drift alert on any metric. Level 2 (operational rules): per-agent monitoring configuration — specific goal-proximity metrics for a given agent type, drift threshold values, escalation rules. Level 3 (agent-internal): the agent's own self-monitoring prompts — "check your current trajectory against the original goal."

**Example:** An agent generates a system architecture document. Level 1 monitoring: latency and error rate — normal. Level 2 monitoring: three goal-proximity metrics defined for this agent type — (a) structural completeness (share of required architecture sections covered), (b) specification fidelity (deviation from the original technical specification), (c) concept novelty (share of introduced concepts with no grounding in the source specification). The agent produced 12 sections out of an expected 15 — metric (a) at 0.8, within acceptable bounds. But metric (b) shows a slow decline: the generated architecture introduces more and more abstractions not rooted in the specification — drift detected, a "trend alert" fires. The monitoring agent notifies the orchestrator: the agent is writing an increasingly abstract document, drifting away from the concrete specification.

Without goal-proximity drift detection, this failure would be invisible: the agent produces text, errors are absent, latency is normal — yet the result steadily diverges from the goal.

**Related Entities:**

- [PATTERN-002](../PATTERN-002-agent-auditor/): the monitoring sub-agent is a specialized instance of the Agent-Auditor — it audits not artifacts but trajectories
- [PATTERN-025](../PATTERN-025-three-level-rule-architecture/): monitoring rules follow the three-level rule architecture — global baseline, per-agent configuration, agent self-monitoring
- [PATTERN-014](../PATTERN-014-reflective-recovery-loop/): triggered by a "critical divergence" monitoring event to force-replan
- [PATTERN-020](../PATTERN-020-ratchet-loop/): drift events feed into the Ratchet Loop as data for refining monitoring thresholds over time

**Experimental Verification:** Required. Test plan: deploy an agent with and without goal-proximity drift detection; inject a gradual specification distortion over the course of 50 tasks. Measure: (1) detection latency — how many tasks elapse from drift onset to alert, (2) false-positive rate, (3) quality of the final artifact under drift with and without detection.

**Application History:** Not applied. Status: raw.
