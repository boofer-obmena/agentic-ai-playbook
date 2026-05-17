---
id: PATTERN-011
title: "Orchestrator-Driven Explicit State Flow"
title_ru: "Паттерн 11. «Оркестратор-дирижёр с явным потоком состояния» (Orchestrator-Driven Explicit State Flow)"
type: pattern
subtype: functional
status: raw
source: "author's development"
date_added: 2026-05-07
version: 1.0
---

# Orchestrator-Driven Explicit State Flow

> **Паттерн 11. «Оркестратор-дирижёр с явным потоком состояния» (Orchestrator-Driven Explicit State Flow)**

**Problem:** In an event-driven choreography architecture, agents communicate with each other directly. When debugging such a system, it is extremely difficult to understand why a particular agent received precisely that data at precisely that moment. In safety-critical systems, such unpredictability is unacceptable.

**Solution:** All interactions between agents are managed by a single centralized component — the Orchestrator, which implements a finite state machine. Agents do not communicate with each other directly. Each agent receives tasks exclusively from the Orchestrator and returns results exclusively to it. The Orchestrator explicitly passes each agent the strictly necessary subset of data — a pinned version, not a reference to mutable state. Every step is recorded in a log suitable for auditing and replay.

**Example:** Request: calculate a credit limit for a counterparty. Step 1: the Orchestrator invokes the analyst agent with a set of financial indicators (version v1.0). Step 2: the Orchestrator invokes the evaluator agent, passing it the analyst's result (v1.0) and the source data (v1.0). The evaluator agent works only with what the Orchestrator explicitly passed to it — this guarantees full reproducibility.

**Experimental Verification:** Simulate the same multi-step process in two modes: event-driven choreography and orchestration. Introduce an artificial network delay at one of the steps. In orchestration mode, the Orchestrator guarantees that the second agent always receives exactly the data produced by the first.

**Application History:** Not applied. This section is populated based on real-world use of the pattern: task context, what worked, what required adjustment, and final conclusions.

### Extension: Goal-Result Paradigm

In classical interaction, a human received text from a model and performed the next step themselves: opened email, pasted the text, clicked send. An agent with a state machine eliminates the human as a "live router." Key requirements: (1) The agent remembers the global goal across all intermediate steps. (2) Each step records an execution status. (3) On an external system error — the agent does not give up but retries with exponential backoff. (4) Intermediate stages are hidden from the user — they see only the final result.
