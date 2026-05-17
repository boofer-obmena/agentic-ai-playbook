---
id: PATTERN-035
title: "Dev-Prod Environment Parity"
title_ru: "Паттерн 35. «Паритет сред разработки и продакшн» (Dev-Prod Environment Parity)"
type: pattern
subtype: engineering
status: raw
source: "Master All 20 Agentic AI Design Patterns (SOURCE-006); author's development"
date_added: 2026-05-07
version: 1.0
related: []
---

# Dev-Prod Environment Parity

> **Паттерн 35. «Паритет сред разработки и продакшн» (Dev-Prod Environment Parity)**

**Problem:** An agent developed and tested in one environment begins to behave differently when moved to production: different tool versions, different file paths, different database connection parameters. The classic "it worked on my machine" situation. In agent systems, this is especially dangerous: the agent can fail silently — producing different results without raising any explicit errors. Moreover, transitioning from the development environment to production requires significant reconfiguration effort, slowing down iterations.

**Solution:** The development environment and the production environment are architecturally identical. This is achieved through: containerization (Docker) with pinned versions of all dependencies; a unified software stack across all machines (identical versions of Ollama, LightRAG, PostgreSQL); configuration via environment variables (a single .env file changes the environment without code changes); a single model registry — the same models with the same quantization on dev and prod. The transition from development to production should require no more than a single configuration change (host address, database URL), not changes to architecture or code. The verification rule: if moving an agent to a new environment requires more than one configuration change — the architecture violates the parity principle.

**Example:** An admin agent is developed and tested on a MacBook (Ollama locally, PostgreSQL in Docker, N8N in Docker). When moving to a Mac Mini, only one parameter changes in docker-compose: OLLAMA_HOST=192.168.0.xxx (the MacBook address on the network). All other components — the same images, the same versions, the same configurations. The agent starts working on the new machine without any additional setup. Its behavior is mathematically identical to that observed in the development environment.

**Experimental Verification:** Required. Develop and debug an agent on one machine. Transfer it to a second machine with different characteristics (different CPU, different RAM). Record: the number of configuration changes required for launch; the divergence in agent behavior between the two environments (should be zero). Acceptable result: one changed parameter (host address), zero divergence in behavior.

**Application History:** Not applied. This section is populated based on real-world use of the pattern: task context, what worked, what required adjustment, and final conclusions.
