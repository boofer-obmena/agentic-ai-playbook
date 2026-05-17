---
id: METHOD-008
title: "Multi-layered Auto-Fix Review"
title_ru: "Многоуровневый контроль автоматических исправлений (Multi-layered Auto-Fix Review)"
type: method
status: raw
subtype: "method / technique"
source: "author's development"
date_added: 2026-05-07
version: 1.0-preview
---

# Multi-layered Auto-Fix Review

> **Многоуровневый контроль автоматических исправлений (Multi-layered Auto-Fix Review)**

**Problem:** The Auditor agent, upon detecting a defect, is capable of independently generating and applying a patch. In most cases, this accelerates the process. However, for critical modules (the financial accounting core, security mechanisms, and components that affect production data), automatically applying a patch without human oversight poses an unacceptable risk.

**Solution:** Each system module is assigned a criticality level (Normal / High / Critical). The patch application process depends on the criticality level. Normal: Auditor generates a patch → QA verifies → automatic application. High: Auditor generates a patch → QA verifies → a review task is created for the Architect → application after approval. Critical: Auditor generates a patch → QA verifies → mandatory Human-in-the-Loop Gate: review task for the Functional Architect → application only after explicit signed approval → notification to the DevOps agent about a critical module change.

**Example:** The Auditor discovers a bug in the tax base calculation module (criticality level: Critical). The Auditor generates a patch. QA verifies the patch against test data — tests pass. The Orchestrator creates a task "Auto-Patch Review" for the Functional Architect of the financial system. The patch remains in a waiting state. Architect approval — patch applied and recorded in the audit log.

**Experimental Verification:** Introduce an intentional bug into a module with Critical criticality level. Run the Auditor. Verify: the patch is generated and passes QA verification, but does not reach the release branch — it remains in the waiting state at the Human-in-the-Loop Gate. The system logs the event "Merge blocked: Critical module, waiting for Human Approver."

**Application History:** Not applied. This section is populated based on real-world use of the method: task context, what worked, what required adjustment, and final conclusions.

**When to Use:** [Requires author refinement — to be finalized in Phase 4]

**Limitations:** [Requires author refinement — to be finalized in Phase 4]

Related Patterns: [Requires author refinement — to be populated in Phase 4]
