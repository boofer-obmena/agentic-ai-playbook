---
id: BACKLOG-012
title: "Command Allowlist — Agent Permission Restriction"
title_ru: "Белый список команд (Command Allowlist) — ограничение прав агента"
type: backlog
status: Candidate
subtype: "method"
source: "ghost reference from PATTERN-026; discovered during Batch 3 translation (2026-05-15)"
date_added: 2026-05-15
version: 1.0
related: ["PATTERN-010", "PATTERN-026"]
---

# Command Allowlist — Agent Permission Restriction

> **Белый список команд (Command Allowlist) — ограничение прав агента**

**Context:** PATTERN-026 (Agent Execution Sandbox), in the "Precondition for Use" section, references "permission restriction via a command allowlist (Pattern И3)." Investigation (2026-05-15) revealed that no entity with this content exists — not among patterns, methods, principles, philosophies, or the backlog. The "И3" reference is dangling; the actual PATTERN-032 (which received number 032 instead of the old "И3") is about RAG, not an allowlist.

**Essence:** This is not a pattern but a method. Restricting an agent's permissions through an allowlist of permitted commands — a security configuration technique for local assistant agents. Unlike full container isolation (PATTERN-026), the allowlist approach applies to agents operating in real time in dialogue with the user.

**Requires elaboration:**
- Format for describing the allowlist (YAML? part of the Tool Manifest?)
- Criteria for including/excluding commands
- Procedure for updating the allowlist when new tools are added
- Interaction with PATTERN-010 (Agent Tool Manifest): allowlist as a reduced manifest or a separate mechanism?

**Status:** Candidate. Requires author decision.
