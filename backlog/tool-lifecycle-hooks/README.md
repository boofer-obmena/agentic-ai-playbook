---
id: BACKLOG-003
title: "Tool Lifecycle Hooks"
title_ru: "Хуки жизненного цикла инструментов (Tool Lifecycle Hooks)"
type: backlog
status: Hypothesis
source: ""
date_added:
version:
related: ["PATTERN-010"]
---

# Tool Lifecycle Hooks

> **Хуки жизненного цикла инструментов (Tool Lifecycle Hooks)**

**Pre-tool hook** — an interceptor before tool execution (e.g., before `git commit` — verify the commit message format). **Post-tool hook** — an interceptor after execution (e.g., after a database write — update the index). Partially implemented on Mac Mini via an API gateway with a command allowlist. Potentially could become a standalone engineering pattern.
