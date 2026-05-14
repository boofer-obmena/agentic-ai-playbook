---
id: PRINCIPLE-011
title: "Think:false/true по типу роли"
type: "principle"
subtype: "архитектурный принцип"
status: "raw"
source: "авторская разработка"
version: "1.0-preview"
date_added: 2026-05-07
related: []
---

# Think:false/true по типу роли

Принцип 6. Think:false/true по типу роли: Рутинный исполнительный агент — think: false. Аналитический или ревьюерный агент — think: true. Не ставить think: true по умолчанию для всех агентов — это повышает стоимость, латентность и непредсказуемость рутинных операций.