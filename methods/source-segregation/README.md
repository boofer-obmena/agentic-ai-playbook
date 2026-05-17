---
id: METHOD-001
title: "Source Segregation"
title_ru: "Сегрегация источников (Source Segregation)"
type: method
status: raw
subtype: "method / technique"
source: "author's development"
date_added: 2026-05-07
version: 1.0-preview
---

# Source Segregation

> **Сегрегация источников (Source Segregation)**

**Problem:** When an incoming data stream mixes statements from different participants — the customer, analyst, and technical specialist — the model cannot determine which participant each claim belongs to. As a result, one participant's requirements may be misattributed to another, and contradictions between positions go unnoticed.

**Solution:** At the preprocessing stage, the incoming data stream is separated into isolated channels. Each channel corresponds to a single source (one participant, one role, or one system). Every data fragment is tagged with a source attribute before being fed to the LLM. This enables the model to correctly attribute claims and detect contradictions between the positions of different participants.

**Example:** The Communicator processes a meeting transcript from a session attended by the customer, architect, and developer. Before being fed to the LLM, the transcript is split into blocks by role: [CUSTOMER]: "We need…", [ARCHITECT]: "I suggest implementing…", [DEVELOPER]: "Technically this is feasible provided that…". The analyst agent sees each participant's position separately and can explicitly identify where positions agree and where they conflict.

**Experimental Verification:** Prepare a meeting transcript with interleaved statements from three participants. Process it in two modes: mixed text and role-tagged text. Measure the accuracy of requirement extraction — how many requirements were correctly attributed to the right participant in each mode.

**Application History:** Not applied. This section is populated based on real-world use of the method: task context, what worked, what required adjustment, and final conclusions.

**When to Use:** [Requires author refinement — to be finalized in Phase 4]

**Limitations:** [Requires author refinement — to be finalized in Phase 4]

Related Patterns: [Requires author refinement — to be populated in Phase 4]
