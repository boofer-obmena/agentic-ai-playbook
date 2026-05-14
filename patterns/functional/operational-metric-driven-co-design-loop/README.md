---
id: PATTERN-015
title: "Operational Metric Driven Co Design Loop"
title_ru: "Паттерн 15. «Сквозной цикл улучшения на основе операционных метрик» (Operational Metric-Driven Co-Design Loop)"
type: pattern
subtype: functional
status: raw
source: авторская разработка
date_added: 2026-05-07
version: 1.0-preview
related: []
---

# Operational Metric Driven Co Design Loop

> **Паттерн 15. «Сквозной цикл улучшения на основе операционных метрик» (Operational Metric-Driven Co-Design Loop)**

**Проблема: Стандартное активное обучение фиксирует ручные правки содержания артефактов, но не замечает неэффективность самого способа действий агента: выбор излишне длинного маршрута, использование GUI там, где есть API.:**



**Решение: Вводится метрика «Эффективности исполнения» (Task Efficiency Score). Любое ручное вмешательство человека, означающее отклонение от плана агента, автоматически создаёт обучающую пару: «Неоптимальный план агента → Предпочтительный план человека». После накопления нескольких примеров агент начинает самостоятельно выбирать более эффективные маршруты.:**



**Related Entities:**

**Implementations:** [implementations/](implementations/)
**Case Studies:** [case-studies/](case-studies/)
**Experiments:** [experiments/](experiments/)