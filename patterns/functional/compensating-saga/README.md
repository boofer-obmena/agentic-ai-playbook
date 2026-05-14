---
id: PATTERN-013
title: "Compensating Saga"
title_ru: "Паттерн 13. «Компенсационная сага» (Compensating Saga for AI-Powered Operations)"
type: pattern
subtype: functional
status: raw
source: авторская разработка
date_added: 2026-05-07
version: 1.0-preview
related: []
---

# Compensating Saga

> **Паттерн 13. «Компенсационная сага» (Compensating Saga for AI-Powered Operations)**

> *[English translation pending. Original Russian text preserved in sections below.]*

## Problem

Многие операции в агентных системах включают вызовы внешних систем, которые нельзя откатить стандартным образом. Если в середине многошаговой операции происходит сбой, система оказывается в частично выполненном состоянии.

## Solution

Каждая высокоуровневая операция, затрагивающая несколько внешних систем, проектируется как Сага. Для каждого шага явно описывается компенсационное действие — операция, которая семантически «отменяет» эффект основного шага. При сбое Оркестратор вызывает компенсационные действия в обратном порядке до достижения согласованного начального состояния.

## Example

Developer Agent создаёт Pull Request (шаг 1). Затем пытается создать связанную задачу в трекере (шаг 2) — трекер недоступен. Оркестратор запускает компенсацию шага 1: закрывает Pull Request с комментарием «Автоматически закрыт: сбой конвейера на шаге 2.»

## Application History

Не применялся. Раздел заполняется по результатам реального использования паттерна: контекст задачи, что сработало, что потребовало корректировки, итоговые выводы.

## Related Entities

**Implementations:** [implementations/](implementations/)
**Case Studies:** [case-studies/](case-studies/)
**Experiments:** [experiments/](experiments/)