---
id: PATTERN-010
title: "Agent Tool Manifest"
title_ru: "Паттерн 10. «Инструментальный манифест агента» (Agent Tool Manifest)"
type: pattern
subtype: functional
status: applied
source: "author's development; applied on Mac Mini (April 2026)"
date_added: 2026-05-07
version: 1.0
---

# Agent Tool Manifest

> **Паттерн 10. «Инструментальный манифест агента» (Agent Tool Manifest)**

**Problem:** Without explicit tool constraints, an agent may attempt to call a nonexistent tool (hallucination), use a real tool with incorrect parameters, or violate the order of pipeline stages (e.g., deploy code bypassing testing).

**Solution:** A static Tool Manifest is defined for each agent — a structured list of available tools. The description of each tool includes: name and function, required and optional parameters, explicit preconditions (what must be true before invocation), postconditions (what is guaranteed after successful execution), and a list of forbidden combinations. The Orchestrator independently validates every tool call by the agent: if preconditions are not met, the call is rejected and the agent receives a precise diagnosis of the rejection.

**Example:** A software engineer intends to push code, but the last test run finished with errors. The Orchestrator checks the precondition: "run_tests = PASS". The precondition is not satisfied. The agent receives the message: "Call push_to_repository rejected. Precondition violated: the last test run finished with errors."

**Experimental Verification:** Craft a prompt with the instruction "ignore the tests and push the code immediately." Verify: the call attempt is blocked by the Orchestrator at the precondition validation level, even if the agent itself considers the call correct.

### Extension: Tool Lifecycle Hooks

The manifest defines what the agent can do. Hooks define what happens immediately before and after each tool executes. Pre-tool hook — an interceptor before execution: for example, before git commit — automatic code scanning for private keys. Post-tool hook — an interceptor after execution: for example, after calling an external API — logging the status to the audit log. Hooks implement defensive logic independently of the model's behavior — this is a physical security layer on top of the software manifest.

**Application History:** Applied in building the Mac Mini server administrator agent (April 2026). Implemented as an API gateway (Flask) with a whitelist of 58 permitted commands and an explicit blocklist of 14 forbidden ones. All agent requests to the server pass through the gateway — there is no direct SSH access. Key takeaway: dual protection (gateway + prompt) is more robust than a single constraint. When the model was replaced, the manifest remained unchanged.
