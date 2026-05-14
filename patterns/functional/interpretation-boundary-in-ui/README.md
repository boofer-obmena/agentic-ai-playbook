---
id: PATTERN-016
title: "Interpretation Boundary In Ui"
title_ru: "Паттерн 16. «Граница интерпретации в интерфейсе» (Interpretation Boundary in UI)"
type: pattern
subtype: functional
status: raw
source: авторская разработка
date_added: 2026-05-07
version: 1.0-preview
related: []
---

# Interpretation Boundary In Ui

> **Паттерн 16. «Граница интерпретации в интерфейсе» (Interpretation Boundary in UI)**

> *[English translation pending — original Russian text preserved in sections below.]*

[Читать на русском](README.ru.md)

## Problem

Языковые модели генерируют единый непрерывный текст, который не разграничивает проверенные факты и вероятностные интерпретации. Пользователь не может отличить «это точно так, потому что зафиксировано в логах» от «это вероятно так». Ложная уверенность приводит к принятию неверных решений.

## Solution

Любой выходной артефакт структурно разделяется на два явных слоя. Слой Фактов: утверждения, подтверждённые сырыми данными — каждый факт содержит ссылку на источник. Слой Выводов: интерпретации, гипотезы, вероятностные оценки — каждый вывод сопровождается Индикатором уверенности (Confidence Score, от 0 до 1). Интерфейс запрещает «смешивать» слои в единый гладкий нарратив.

## Application History

Не применялся. Раздел заполняется по результатам реального использования паттерна: контекст задачи, что сработало, что потребовало корректировки, итоговые выводы.

## Related Entities

**Implementations:** [implementations/](implementations/)
**Case Studies:** [case-studies/](case-studies/)
**Experiments:** [experiments/](experiments/)