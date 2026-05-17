---
id: PATTERN-041
title: "Adaptive Load Management (Circuit Breaker)"
title_ru: "Паттерн 41. «Адаптивное управление нагрузкой (Circuit Breaker)» (Adaptive Load Management)"
type: pattern
subtype: engineering
status: raw
source: "Master All 20 Agentic AI Design Patterns (SOURCE-006); author's development"
date_added: 2026-05-07
version: 1.0
related: []
---

# Adaptive Load Management (Circuit Breaker)

> **Паттерн 41. «Адаптивное управление нагрузкой (Circuit Breaker)» (Adaptive Load Management)**

**Problem:** When an external system or model is overloaded, the agent continues sending requests, worsening the situation. Repeated retries to an unavailable service lead to a cascading failure: the request queue grows, resources are exhausted, the system does not recover.

**Solution:** The Circuit Breaker pattern is implemented with three states. Closed (normal): requests pass through, errors are counted. Open (failure mode): when errors exceed the threshold within the configured time window — the Circuit Breaker transitions to Open. All requests are immediately rejected with the response "service temporarily unavailable," without attempting a call. Half-Open (probe): after a defined interval, the Circuit Breaker lets through a test request. On success — transitions to Closed. On failure — transitions back to Open.

**Example:** To be developed.

**Related Entities:** To be developed.

**Precondition:** To be developed.

**Experimental Verification:** Required. Simulate the unavailability of an external API. Verify: after N errors, the Circuit Breaker transitions to Open, requests are rejected immediately, the state transition is recorded in the log. After the API recovers — automatic transition to Closed.

**Application History:** Not applied. This section is populated based on real-world use of the pattern: task context, what worked, what required adjustment, and final conclusions.
