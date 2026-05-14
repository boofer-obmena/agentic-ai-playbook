---
id: PATTERN-041
title: "Adaptive Load Management"
title_ru: "Паттерн И12. «Адаптивное управление нагрузкой (Circuit Breaker)» (Adaptive Load Management)"
type: pattern
subtype: engineering
status: raw
source: авторская разработка
date_added: 2026-05-07
version: 1.0-preview
related: []
---

# Adaptive Load Management

> **Паттерн И12. «Адаптивное управление нагрузкой (Circuit Breaker)» (Adaptive Load Management)**

**Проблема: При перегрузке внешней системы или модели агент продолжает отправлять запросы, усугубляя ситуацию. Повторные попытки при недоступном сервисе приводят к каскадному отказу: очередь запросов растёт, ресурсы истощаются, система не восстанавливается.:**



**Решение: Реализуется паттерн Circuit Breaker (Автоматический выключатель) с тремя состояниями. Closed (норма): запросы проходят, ошибки подсчитываются. Open (аварийный режим): при превышении порога ошибок за период — Circuit Breaker переходит в Open. Все запросы немедленно отклоняются с диагнозом «сервис временно недоступен», без попыток вызова. Half-Open (проверка): через заданный интервал Circuit Breaker пропускает пробный запрос. При успехе — возвращается в Closed. При неудаче — снова Open.:**



**Экспериментальная проверка: Симулировать недоступность внешнего API. Проверить: после N ошибок Circuit Breaker переходит в Open, запросы отклоняются немедленно, в журнале фиксируется переход состояния. После восстановления API — автоматический переход в Closed.:**



**Related Entities:**

**Implementations:** [implementations/](implementations/)
**Case Studies:** [case-studies/](case-studies/)
**Experiments:** [experiments/](experiments/)