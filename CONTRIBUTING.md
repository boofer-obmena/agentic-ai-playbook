# Contributing to Agentic AI Playbook

## Types of Contributions

- **New patterns** — architectural solutions you've validated in practice
- **Pattern improvements** — refinements, counterexamples, experimental results
- **Methods** — implementation techniques that worked for you
- **Philosophies** — broader principles you've derived
- **Translations** — Russian ↔ English translations of existing entities
- **Sources** — annotated references to papers, books, talks

## How to Contribute

1. Fork the repo
2. Create a branch: `pattern/my-new-pattern` or `fix/clarify-routing`
3. Create a folder for your entity with `README.md` + `README.ru.md` inside
4. Follow the entity template (see any existing pattern folder for the format)
5. Submit a PR with a clear description of what you're adding and why

## Entity Structure

Each entity is a folder containing:

```
entity-name/
├── README.md            ← description in English (required)
├── README.ru.md         ← description in Russian (required)
├── implementations/     ← runnable code, configs, workflows (optional)
├── case-studies/        ← real-world application reports (optional)
└── experiments/         ← benchmarks, metrics, verification results (optional)
```

## Entity Template

```markdown
---
id: PATTERN-001
title: "Artifact Provenance Chain"
title_ru: "Цепочка происхождения артефакта"
type: pattern
subtype: functional
status: raw
source: author
date_added: 2026-05-07
version: 1.0
related: []
---

# Artifact Provenance Chain

> **Цепочка происхождения артефакта**

**Problem:** ...

**Solution:** ...

**Example:** ...

**Experimental Verification:** ...

**Application History:** ...

**Related Entities:** ...

**Implementations:** [implementations/](implementations/)
**Case Studies:** [case-studies/](case-studies/)
**Experiments:** [experiments/](experiments/)
```

## Language Policy

- All entities exist in both English and Russian
- English is the primary language of the repository
- If you submit an entity in one language only, mark it `needs-translation` and we'll translate it

## Statuses

- `raw` — first draft, needs validation
- `review` — under peer review
- `verified` — experimentally confirmed
- `stable` — battle-tested in production
