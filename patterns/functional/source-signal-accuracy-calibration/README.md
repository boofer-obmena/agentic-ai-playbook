---
id: PATTERN-018
title: "Source Signal Accuracy Calibration"
title_ru: "Паттерн 18. «Калибровка источников по точности сигнала» (Source Signal Accuracy Calibration)"
type: pattern
subtype: functional
status: raw
source: авторская разработка
date_added: 2026-05-07
version: 1.0-preview
related: []
---

# Source Signal Accuracy Calibration

> **Паттерн 18. «Калибровка источников по точности сигнала» (Source Signal Accuracy Calibration)**

**Проблема: Все источники данных поступают в систему как равноценные, хотя их достоверность принципиально различается. Запись в транзакционной БД и жалоба в рабочем чате — принципиально разные уровни достоверности.:**



**Решение: Каждому источнику присваивается коэффициент точности сигнала (Accuracy Score, от 0 до 1). Примерная шкала: 1.0 — транзакционные логи; 0.8 — формальные технические документы; 0.7 — структурированные отчёты; 0.5 — неструктурированные документы; 0.3 — рабочие чаты и мессенджеры. Формировать утверждения в «Слое фактов» можно только на основании источников с коэффициентом выше заданного порога (например, 0.7).:**



**Related Entities:**

**Implementations:** [implementations/](implementations/)
**Case Studies:** [case-studies/](case-studies/)
**Experiments:** [experiments/](experiments/)