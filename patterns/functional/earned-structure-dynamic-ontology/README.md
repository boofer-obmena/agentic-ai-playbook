---
id: PATTERN-017
title: "Earned Structure Dynamic Ontology"
title_ru: "Паттерн 17. «Динамическая онтология с заслуженной структурой» (Earned Structure Dynamic Ontology)"
type: pattern
subtype: functional
status: raw
source: авторская разработка
date_added: 2026-05-07
version: 1.0-preview
related: []
---

# Earned Structure Dynamic Ontology

> **Паттерн 17. «Динамическая онтология с заслуженной структурой» (Earned Structure Dynamic Ontology)**

> *[English translation pending. Original Russian text preserved in sections below.]*

## Problem

Жёсткие заранее определённые онтологии не способны отражать новые связи, которые возникают в процессе работы системы. Необходим механизм, который позволяет органически выявлять новые связи, не разрушая проверенную структуру.

## Solution

Онтология разделяется на два уровня. Жёсткое ядро: зафиксированные, многократно подтверждённые связи. Изменяются только по решению Архитектора. Периферия предположений: динамические гипотетические связи, автоматически обнаруженные Аудитором. Каждая гипотеза имеет счётчик подтверждений и после N независимых подтверждений предлагается к переводу в жёсткое ядро (но переводится только после одобрения Архитектором).

## Application History

Не применялся. Раздел заполняется по результатам реального использования паттерна: контекст задачи, что сработало, что потребовало корректировки, итоговые выводы.

## Related Entities

**Implementations:** [implementations/](implementations/)
**Case Studies:** [case-studies/](case-studies/)
**Experiments:** [experiments/](experiments/)