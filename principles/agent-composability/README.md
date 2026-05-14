---
id: PRINCIPLE-007
title: "Agent Composability"
title_ru: "Лимит итераций как предохранитель"
type: principle
subtype: "архитектурный принцип"
status: raw
source: авторская разработка
date_added: 2026-05-07
version: 1.0-preview
related: []
---

# Agent Composability

> **Лимит итераций как предохранитель**

> *[English translation pending. Original Russian text preserved in sections below.]*

## Essence

Принцип 2. Лимит итераций как предохранитель: Агент без жёсткого ограничения числа итераций — системный риск. Жёсткий лимит итераций — не ограничение автономности агента, а её обязательное условие. При проектировании любого агентного цикла первым делом определить максимальное число итераций и поведение агента при достижении лимита (остановка, эскалация, запись в лог).

## Related Entities
