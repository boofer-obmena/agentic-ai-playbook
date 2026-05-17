---
id: ROOT
title: "Agentic AI Playbook"
type: index
status: stable
version: "1.0"
---

# Agentic AI Playbook

An open knowledge base for designing AI agent systems — patterns, methods, philosophies, and principles. Not a textbook, not a gold standard. A living system that grows with every source cross-validated.

[Читать на русском](README.ru.md)

## What's Inside

- **Patterns** — architectural solutions: component structures, interaction protocols, responsibility distribution
- **Methods** — implementation techniques: how to do something inside a component
- **Philosophies** — broader principles above concrete architectural decisions
- **Principles** — foundational design axioms
- **Backlog** — unresolved problems and future research directions
- **Anti-patterns** — what NOT to do and why
- **Sources** — annotated bibliography of materials that shaped the Playbook

## Quick Start

Pick your entry point:

- **I'm new to agent design** → Start with [Artifact Provenance Chain](patterns/functional/artifact-provenance-chain/) and [Smart Dispatcher](patterns/functional/smart-dispatcher/)
- **I'm designing a multi-agent system** → [Agent Debate](patterns/functional/agent-debate/), [Structural Parallelization](patterns/functional/structural-parallelization-specialization/)
- **I'm debugging agent reliability** → [Reflexive Recovery](patterns/functional/reflexive-recovery-plan-revision/), [Active Learning](patterns/engineering/active-learning-via-artifact-correction/), [Agent Quality Gate](patterns/functional/agent-quality-gate-pipeline/)
- **I need a security model** → [Agent Security Perimeter](patterns/functional/agent-security-perimeter/)
- **I want to see the full index** → Scroll down

## How This Playbook Works

Every entity follows a consistent structure: Problem → Solution → Example → Experimental Verification → Application History.

Entities are cross-referenced: a pattern links to the methods it uses, the philosophies it embodies, and the sources that shaped it.

Statuses:
- `raw` — first draft, needs validation
- `review` — under peer review
- `verified` — experimentally confirmed
- `stable` — battle-tested in production

## Philosophies (7)

| PHILOSOPHY-002 | [Liberation from Administrative Routine](philosophy/admin-routine-liberation/) | raw |
| PHILOSOPHY-001 | [Domain Primacy (DDD)](philosophy/domain-primacy/) | raw |
| PHILOSOPHY-007 | [Trust Between Human and Agent as an Evolving System Variable](philosophy/evolving-human-agent-trust/) | raw |
| PHILOSOPHY-003 | [Honest Uncertainty](philosophy/honest-uncertainty/) | raw |
| PHILOSOPHY-006 | [Primacy of Iterative Self-Deepening over Single-Pass Generation](philosophy/iterative-self-deepening/) | raw |
| PHILOSOPHY-005 | [Semantic Density (Intelligence per Byte)](philosophy/semantic-density/) | raw |
| PHILOSOPHY-004 | [Throughput over Capacity](philosophy/throughput-over-capacity/) | raw |

## Principles (11)

| PRINCIPLE-001 | [Active Traceability](principles/active-traceability/) | raw |
| PRINCIPLE-010 | [Audit Log as the Foundation of Trust](principles/audit-log-as-trust-foundation/) | raw |
| PRINCIPLE-008 | [Automate the Verifiable](principles/automate-the-verifiable/) | raw |
| PRINCIPLE-005 | [Explicit State Flow](principles/explicit-state-flow/) | raw |
| PRINCIPLE-004 | [Immutability of Facts and Computability of Projections](principles/immutable-facts-computable-projections/) | raw |
| PRINCIPLE-009 | [Input Quality Determines Output Quality](principles/input-quality-determines-output/) | raw |
| PRINCIPLE-007 | [Iteration Limit as Safeguard](principles/iteration-limit-as-safeguard/) | raw |
| PRINCIPLE-002 | [Managed Lifecycle](principles/managed-lifecycle/) | raw |
| PRINCIPLE-003 | [Resource Governance](principles/resource-security/) | raw |
| PRINCIPLE-006 | [Steerability over Specialization](principles/steerability-over-specialization/) | raw |
| PRINCIPLE-011 | [Think:false/true by Role Type](principles/think-mode-by-role-type/) | raw |

## Pattern Index

### Functional Patterns (38)

| PATTERN-012 | [Agent Boundary Contract](patterns/functional/agent-boundary-contract/) | raw |
| PATTERN-021 | [Agent Debate](patterns/functional/agent-debate/) | raw |
| PATTERN-026 | [Agent Execution Sandbox](patterns/functional/agent-execution-sandbox/) | raw |
| PATTERN-051 | [Agent Quality Gate Pipeline](patterns/functional/agent-quality-gate-pipeline/) | raw |
| PATTERN-050 | [Agent Security Perimeter](patterns/functional/agent-security-perimeter/) | raw |
| PATTERN-010 | [Agent Tool Manifest](patterns/functional/agent-tool-manifest/) | applied |
| PATTERN-029 | [Append-Only Session Log](patterns/functional/append-only-session-log/) | raw |
| PATTERN-001 | [Artifact Provenance Chain](patterns/functional/artifact-provenance-chain/) | raw |
| PATTERN-024 | [Closed-Loop Co-Testing](patterns/functional/closed-loop-co-testing/) | raw |
| PATTERN-013 | [Compensating Saga for AI-Powered Operations](patterns/functional/compensating-saga/) | raw |
| PATTERN-049 | [Cross-Domain Cognitive Borrowing](patterns/functional/cross-domain-cognitive-borrowing/) | raw |
| PATTERN-048 | [Dynamic Task Queue Prioritizer](patterns/functional/dynamic-queue-prioritizer/) | raw |
| PATTERN-017 | [Earned Structure Dynamic Ontology](patterns/functional/earned-structure-dynamic-ontology/) | raw |
| PATTERN-044 | [Evolving Human-Agent Trust Loop](patterns/functional/evolving-human-agent-trust/) | raw |
| PATTERN-045 | [Unified Agent Memory Model: Four Cognitive Levels](patterns/functional/four-level-agent-memory/) | raw |
| PATTERN-008 | [Ground Truth vs. Computed Projection](patterns/functional/ground-truth-computed-projection/) | raw |
| PATTERN-019 | [Hardware-Aware Lifecycle Separation](patterns/functional/hardware-aware-lifecycle-separation/) | raw |
| PATTERN-009 | [Immutable State & Append-Only Artifacts](patterns/functional/immutable-state-append-only-artifacts/) | raw |
| PATTERN-016 | [Interpretation Boundary in UI](patterns/functional/interpretation-boundary-ui/) | raw |
| PATTERN-005 | [Multi-Layered Validation Gateway](patterns/functional/multi-layered-validation-gateway/) | raw |
| PATTERN-023 | [Multi-Variant Plan Generator](patterns/functional/multi-variant-plan-generator/) | raw |
| PATTERN-003 | [Operation Driven Lifecycle](patterns/functional/operation-driven-lifecycle/) | raw |
| PATTERN-015 | [Operational Metric-Driven Co-Design Loop](patterns/functional/operational-metric-co-design-loop/) | raw |
| PATTERN-011 | [Orchestrator-Driven Explicit State Flow](patterns/functional/orchestrator-explicit-state-flow/) | raw |
| PATTERN-022 | [Proactive Goal Interpreter](patterns/functional/proactive-goal-interpreter/) | raw |
| PATTERN-028 | [Prompt Cache Optimization](patterns/functional/prompt-cache-optimization/) | raw |
| PATTERN-020 | [Ratchet Loop](patterns/functional/ratchet-loop/) | applied |
| PATTERN-002 | [Recursive Quality Oversight](patterns/functional/recursive-quality-oversight/) | raw |
| PATTERN-014 | [Reflexive Recovery with Plan Revision](patterns/functional/reflexive-recovery-plan-revision/) | raw |
| PATTERN-027 | [Semantic Context Compaction](patterns/functional/semantic-context-compaction/) | raw |
| PATTERN-043 | [Single-Role Reflective Deepening](patterns/functional/single-role-reflective-deepening/) | raw |
| PATTERN-006 | [Smart Dispatcher](patterns/functional/smart-dispatcher/) | raw |
| PATTERN-018 | [Source Signal Accuracy Calibration](patterns/functional/source-signal-accuracy-calibration/) | raw |
| PATTERN-046 | [Structural Parallelization with Specialization](patterns/functional/structural-parallelization-specialization/) | raw |
| PATTERN-047 | [Targeted Monitoring with Drift Detection](patterns/functional/targeted-monitoring-drift-detection/) | raw |
| PATTERN-007 | [Test Case as Oracle Artifact](patterns/functional/test-case-oracle-artifact/) | raw |
| PATTERN-025 | [Three-Layer Agent Rules Architecture](patterns/functional/three-layer-agent-rules/) | applied |
| PATTERN-004 | [Transactional Composite Operation](patterns/functional/transactional-composite-operation/) | raw |

### Engineering Patterns (13)

| PATTERN-030 | [Active Learning via Artifact Correction](patterns/engineering/active-learning-via-artifact-correction/) | raw |
| PATTERN-041 | [Adaptive Load Management (Circuit Breaker)](patterns/engineering/adaptive-load-management/) | raw |
| PATTERN-034 | [Agent First-Token Response](patterns/engineering/agent-first-token-response/) | raw |
| PATTERN-032 | [Agentic RAG with Tool-Augmented Closed Loop](patterns/engineering/agentic-rag-tool-augmented/) | raw |
| PATTERN-035 | [Dev-Prod Environment Parity](patterns/engineering/dev-prod-environment-parity/) | raw |
| PATTERN-039 | [Generator-Executor Pattern](patterns/engineering/generator-executor/) | raw |
| PATTERN-038 | [Gradient Data Storage](patterns/engineering/gradient-data-storage/) | raw |
| PATTERN-042 | [Idea File as Executable Architecture](patterns/engineering/idea-file-executable-architecture/) | raw |
| PATTERN-036 | [Intelligent Model Routing](patterns/engineering/intelligent-model-routing/) | raw |
| PATTERN-037 | [Multi-Vector Semantic Index](patterns/engineering/multi-vector-semantic-index/) | raw |
| PATTERN-031 | [Seamless Model Rotation in Vector Store](patterns/engineering/seamless-model-rotation/) | raw |
| PATTERN-033 | [Semantic Query Fan-out](patterns/engineering/semantic-query-fan-out/) | raw |
| PATTERN-040 | [Spatial-Visual UI Memory](patterns/engineering/spatial-visual-ui-memory/) | raw |

## Method Index (16)

| METHOD-012 | [Agent Debugging and Alerting](methods/agent-debugging-and-alerting/) | raw |
| METHOD-007 | [Agent State Checkpointing](methods/agent-state-checkpointing/) | raw |
| METHOD-010 | [Chunking Strategies](methods/chunking-strategies/) | raw |
| METHOD-004 | [Constrained Templating with Evidence](methods/constrained-templating-with-evidence/) | raw |
| METHOD-011 | [Context Window and Prompt Cache](methods/context-window-and-prompt-cache/) | raw |
| METHOD-003 | [Data Canonicalization for LLM](methods/data-canonization-for-llm/) | raw |
| METHOD-006 | [Disk-Optimized Vector Index for Cold Memory](methods/disk-optimized-vector-index-for-cold-memory/) | raw |
| METHOD-009 | [Data Processing Pipeline and Embedding Strategies](methods/embedding-pipeline-and-strategies/) | raw |
| METHOD-014 | [Experiment Design Standard](methods/experiment-design-standard/) | raw |
| METHOD-016 | [Techniques of Forced Reasoning (CoT, ToT, Self-Consistency)](methods/forced-reasoning-techniques/) | raw |
| METHOD-015 | [Guided Exploration of Unknown Unknowns](methods/guided-exploration-of-unknown-unknowns/) | raw |
| METHOD-002 | [Lightweight Security Perimeter](methods/lightweight-security-perimeter/) | raw |
| METHOD-008 | [Multi-layered Auto-Fix Review](methods/multi-layered-auto-fix-review/) | raw |
| METHOD-013 | [Rule Persistence and Evolution](methods/rule-persistence-and-evolution/) | raw |
| METHOD-001 | [Source Segregation](methods/source-segregation/) | raw |
| METHOD-005 | [Structure-Aware Document Preprocessing](methods/structure-aware-document-preprocessing/) | raw |

## Backlog (12)

| BACKLOG-005 | [Agent Autonomy Progression](backlog/agent-autonomy-progression/) | Observation |
| BACKLOG-009 | [Agent Collective Memory](backlog/agent-collective-memory/) | Idea |
| BACKLOG-007 | [Agent in a Shared Communication Channel](backlog/agent-in-shared-channel/) | Hypothesis |
| BACKLOG-002 | [Agent Memory as a Critical Asset](backlog/agent-memory-as-critical-asset/) | Observation |
| BACKLOG-010 | [Agent Self-Testing Before Deployment](backlog/agent-self-testing/) | Idea |
| BACKLOG-012 | [Command Allowlist — Agent Permission Restriction](backlog/command-allowlist/) | Candidate |
| BACKLOG-001 | [Dispatcher-by-Goal (Analog Dispatcher)](backlog/dispatcher-by-goal/) | Hypothesis |
| BACKLOG-004 | [Goal-Result Paradigm](backlog/goal-result-paradigm/) | Hypothesis |
| BACKLOG-006 | [Jagged Intelligence](backlog/jagged-intelligence/) | Observation |
| BACKLOG-008 | [Spawn-Restrict-Collect](backlog/spawn-restrict-collect/) | Hypothesis |
| BACKLOG-003 | [Tool Lifecycle Hooks](backlog/tool-lifecycle-hooks/) | Hypothesis |
| BACKLOG-011 | [Upstream Loop: From Vague Goal to Measurable KPIs (Communicator → Task Formulator)](backlog/upstream-loop/) | Idea |

## Anti-patterns (1)

| ANTIPATTERN-001 | [Overpowered Model Anti-Pattern](antipatterns/overpowered-model/) | applied |

## Appendices (1)

|  | [Appendix A. Agent System Role Catalog](appendices/agent-role-catalog/) | raw |

## How to Contribute

See [CONTRIBUTING.md](CONTRIBUTING.md).

## License

MIT — see [LICENSE](LICENSE).

## Contact

- GitHub: [@boofer-obmena](https://github.com/boofer-obmena)
