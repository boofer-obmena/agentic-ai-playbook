---
id: ROOT
title: "PlayBook Архитектора AI-агентов"
type: index
status: stable
version: "1.0"
---

# PlayBook Архитектора AI-агентов

Открытая база знаний по проектированию AI-агентных систем: паттерны, методы, философии и принципы. Не учебник, не золотой стандарт. Живая система, растущая с каждым перекрёстно проверенным источником.

[Read in English](README.md)

## Что внутри

- **Паттерны** — архитектурные решения: структуры компонентов, протоколы взаимодействия, распределение ответственности
- **Методы** — техники реализации: как сделать что-то внутри компонента
- **Философии** — широкие принципы над конкретными архитектурными решениями
- **Принципы** — фундаментальные аксиомы проектирования
- **Бэклог** — нерешённые проблемы и направления будущих исследований
- **Антипаттерны** — чего НЕ делать и почему
- **Источники** — аннотированная библиография материалов, повлиявших на PlayBook

## Быстрый старт

Выберите точку входа:

- **Я новичок в проектировании агентов** → Начните с [Цепочка происхождения артефакта](patterns/functional/artifact-provenance-chain/) и [Умный диспетчер](patterns/functional/smart-dispatcher/)
- **Я проектирую мульти-агентную систему** → [Дебаты агентов](patterns/functional/agent-debate/), [Структурная параллелизация](patterns/functional/structural-parallelization-specialization/)
- **Я отлаживаю надёжность агента** → [Рефлексивное восстановление](patterns/functional/reflexive-recovery-plan-revision/), [Активное обучение](patterns/engineering/active-learning-via-artifact-correction/), [Контроль качества](patterns/functional/agent-quality-gate-pipeline/)
- **Мне нужна модель безопасности** → [Периметр безопасности агента](patterns/functional/agent-security-perimeter/)
- **Хочу увидеть полный индекс** → Смотрите ниже

## Как устроен PlayBook

Каждая сущность следует единой структуре: Проблема → Решение → Пример → Экспериментальная проверка → История применения.

Сущности перекрёстно связаны: паттерн ссылается на методы, которые использует, философии, которые воплощает, и источники, которые его сформировали.

Статусы:
- `raw` — первый черновик, требуется валидация
- `review` — на рецензировании
- `verified` — экспериментально подтверждён
- `stable` — проверен в бою

## Философии (7)

| PHILOSOPHY-002 | [Освобождение от административной рутины](philosophy/admin-routine-liberation/) | raw |
| PHILOSOPHY-001 | [Первичность предметной области (DDD)](philosophy/domain-primacy/) | raw |
| PHILOSOPHY-007 | [Доверие между человеком и агентом как эволюционирующая переменная системы](philosophy/evolving-human-agent-trust/) | raw |
| PHILOSOPHY-003 | [Принцип честной неуверенности (Honest Uncertainty)](philosophy/honest-uncertainty/) | raw |
| PHILOSOPHY-006 | [Первичность итеративного самоуглубления над однопроходной генерацией](philosophy/iterative-self-deepening/) | raw |
| PHILOSOPHY-005 | [Принцип смысловой плотности («Интеллект на байт»)](philosophy/semantic-density/) | raw |
| PHILOSOPHY-004 | [Принцип пропускной способности над ёмкостью](philosophy/throughput-over-capacity/) | raw |

## Принципы (11)

| PRINCIPLE-001 | [Активная прослеживаемость](principles/active-traceability/) | raw |
| PRINCIPLE-010 | [Журнал аудита как основа доверия](principles/audit-log-as-trust-foundation/) | raw |
| PRINCIPLE-008 | [Автоматизируй верифицируемое](principles/automate-the-verifiable/) | raw |
| PRINCIPLE-005 | [Принцип явного потока состояния](principles/explicit-state-flow/) | raw |
| PRINCIPLE-004 | [Принцип неизменяемости фактов и вычисляемости проекций](principles/immutable-facts-computable-projections/) | raw |
| PRINCIPLE-009 | [Качество входа определяет качество выхода](principles/input-quality-determines-output/) | raw |
| PRINCIPLE-007 | [Лимит итераций как предохранитель](principles/iteration-limit-as-safeguard/) | raw |
| PRINCIPLE-002 | [Управляемый жизненный цикл](principles/managed-lifecycle/) | raw |
| PRINCIPLE-003 | [Ресурсная безопасность](principles/resource-security/) | raw |
| PRINCIPLE-006 | [Управляемость важнее специализации](principles/steerability-over-specialization/) | raw |
| PRINCIPLE-011 | [Think:false/true по типу роли](principles/think-mode-by-role-type/) | raw |

## Индекс паттернов

### Функциональные паттерны (38)

| PATTERN-012 | [Паттерн 12. «Контракт на границе как фейс-контроль агента» (Agent Boundary Contract)](patterns/functional/agent-boundary-contract/) | raw |
| PATTERN-021 | [Паттерн 21. «Дебаты агентов» (Agent Debate)](patterns/functional/agent-debate/) | raw |
| PATTERN-026 | [Паттерн 26. «Изолированная песочница агента» (Agent Execution Sandbox)](patterns/functional/agent-execution-sandbox/) | raw |
| PATTERN-051 | [Контроль качества в жизненном цикле агента](patterns/functional/agent-quality-gate-pipeline/) | raw |
| PATTERN-050 | [Периметр безопасности агентной системы](patterns/functional/agent-security-perimeter/) | raw |
| PATTERN-010 | [Паттерн 10. «Инструментальный манифест агента» (Agent Tool Manifest)](patterns/functional/agent-tool-manifest/) | applied |
| PATTERN-029 | [Паттерн 29. «Журнал сессии в режиме только-добавления» (Append-Only Session Log)](patterns/functional/append-only-session-log/) | raw |
| PATTERN-001 | [Паттерн 1. «Цепочка происхождения артефакта» (Artifact Provenance Chain)](patterns/functional/artifact-provenance-chain/) | raw |
| PATTERN-024 | [Паттерн 24. «Замкнутый цикл совместного тестирования» (Closed-Loop Co-Testing)](patterns/functional/closed-loop-co-testing/) | raw |
| PATTERN-013 | [Паттерн 13. «Компенсационная сага» (Compensating Saga for AI-Powered Operations)](patterns/functional/compensating-saga/) | raw |
| PATTERN-049 | [Кросс-доменное заимствование мышления](patterns/functional/cross-domain-cognitive-borrowing/) | raw |
| PATTERN-048 | [Динамический приоритизатор очереди задач](patterns/functional/dynamic-queue-prioritizer/) | raw |
| PATTERN-017 | [Паттерн 17. «Динамическая онтология с заслуженной структурой» (Earned Structure Dynamic Ontology)](patterns/functional/earned-structure-dynamic-ontology/) | raw |
| PATTERN-044 | [Человеко-агентный контур с эволюционирующим доверием](patterns/functional/evolving-human-agent-trust/) | raw |
| PATTERN-045 | [Единая модель памяти агента: четыре когнитивных уровня](patterns/functional/four-level-agent-memory/) | raw |
| PATTERN-008 | [Паттерн 8. «Фундаментальный источник против вычисляемой проекции» (Ground Truth vs. Computed Projection)](patterns/functional/ground-truth-computed-projection/) | raw |
| PATTERN-019 | [Паттерн 19. «Аппаратно-осознанное разделение фаз жизненного цикла модели» (Hardware-Aware Lifecycle Separation)](patterns/functional/hardware-aware-lifecycle-separation/) | raw |
| PATTERN-009 | [Паттерн 9. «Неизменяемые состояния и версионирование артефактов» (Immutable State & Append-Only Artifacts)](patterns/functional/immutable-state-append-only-artifacts/) | raw |
| PATTERN-016 | [Паттерн 16. «Граница интерпретации в интерфейсе» (Interpretation Boundary in UI)](patterns/functional/interpretation-boundary-ui/) | raw |
| PATTERN-005 | [Паттерн 5. «Многоуровневый защитный контур (Валидатор)» (Multi-layered Validation Gateway)](patterns/functional/multi-layered-validation-gateway/) | raw |
| PATTERN-023 | [Паттерн 23. «Многовариантный генератор плана» (Multi-Variant Plan Generator)](patterns/functional/multi-variant-plan-generator/) | raw |
| PATTERN-003 | [Паттерн 3. «Жизненный цикл, управляемый операциями» (Operation-Driven Lifecycle)](patterns/functional/operation-driven-lifecycle/) | raw |
| PATTERN-015 | [Паттерн 15. «Сквозной цикл улучшения на основе операционных метрик» (Operational Metric-Driven Co-Design Loop)](patterns/functional/operational-metric-co-design-loop/) | raw |
| PATTERN-011 | [Паттерн 11. «Оркестратор-дирижёр с явным потоком состояния» (Orchestrator-Driven Explicit State Flow)](patterns/functional/orchestrator-explicit-state-flow/) | raw |
| PATTERN-022 | [Паттерн 22. «Проактивный интерпретатор цели» (Proactive Goal Interpreter)](patterns/functional/proactive-goal-interpreter/) | raw |
| PATTERN-028 | [Паттерн 28. «Статика вперёд, динамика в конец» (Prompt Cache Optimization)](patterns/functional/prompt-cache-optimization/) | raw |
| PATTERN-020 | [Паттерн 20. «Ratchet Loop / Храповой цикл самоулучшения» (Ratchet Loop)](patterns/functional/ratchet-loop/) | applied |
| PATTERN-002 | [Паттерн 2. «Активная прослеживаемость: Агент-Аудитор» (Recursive Quality Oversight)](patterns/functional/recursive-quality-oversight/) | raw |
| PATTERN-014 | [Паттерн 14. «Рефлексивный цикл восстановления с пересмотром плана» (Reflexive Recovery with Plan Revision)](patterns/functional/reflexive-recovery-plan-revision/) | raw |
| PATTERN-027 | [Паттерн 27. «Семантически умное сжатие контекста» (Semantic Context Compaction)](patterns/functional/semantic-context-compaction/) | raw |
| PATTERN-043 | [Рефлексивное самоуглубление в рамках одной роли](patterns/functional/single-role-reflective-deepening/) | raw |
| PATTERN-006 | [Паттерн 6. «Фильтр-подбор (Умный диспетчер)» (Smart Dispatcher)](patterns/functional/smart-dispatcher/) | raw |
| PATTERN-018 | [Паттерн 18. «Калибровка источников по точности сигнала» (Source Signal Accuracy Calibration)](patterns/functional/source-signal-accuracy-calibration/) | raw |
| PATTERN-046 | [Структурная параллелизация со специализацией](patterns/functional/structural-parallelization-specialization/) | raw |
| PATTERN-047 | [Целевой мониторинг с дрейф-детекцией](patterns/functional/targeted-monitoring-drift-detection/) | raw |
| PATTERN-007 | [Паттерн 7. «Тест-кейс как артефакт со встроенным оракулом» (Test Case as Oracle Artifact)](patterns/functional/test-case-oracle-artifact/) | raw |
| PATTERN-025 | [Паттерн 25. «Трёхуровневая архитектура правил агента» (Three-Layer Agent Rules Architecture)](patterns/functional/three-layer-agent-rules/) | applied |
| PATTERN-004 | [Паттерн 4. «Композитная операция в единой транзакции» (Transactional Composite Operation)](patterns/functional/transactional-composite-operation/) | raw |

### Инженерные паттерны (13)

| PATTERN-030 | [Паттерн 030. «Активное обучение через коррекцию артефакта» (Active Learning via Artifact Correction)](patterns/engineering/active-learning-via-artifact-correction/) | raw |
| PATTERN-041 | [Паттерн 41. «Адаптивное управление нагрузкой (Circuit Breaker)» (Adaptive Load Management)](patterns/engineering/adaptive-load-management/) | raw |
| PATTERN-034 | [Паттерн 34. «Первый отклик агента» (Agent First-Token Response)](patterns/engineering/agent-first-token-response/) | raw |
| PATTERN-032 | [Паттерн 032. «Агентный поиск с инструментальным замкнутым циклом» (Agentic RAG with Tool-Augmented Closed Loop)](patterns/engineering/agentic-rag-tool-augmented/) | raw |
| PATTERN-035 | [Паттерн 35. «Паритет сред разработки и продакшн» (Dev-Prod Environment Parity)](patterns/engineering/dev-prod-environment-parity/) | raw |
| PATTERN-039 | [Паттерн 39. «Генератор-Исполнитель» (Generator-Executor Pattern)](patterns/engineering/generator-executor/) | raw |
| PATTERN-038 | [Паттерн 38. «Градиентное хранение данных» (Gradient Data Storage)](patterns/engineering/gradient-data-storage/) | raw |
| PATTERN-042 | [Паттерн 42. «Файл идеи как исполнимый архитектурный артефакт» (Idea File as Executable Architecture)](patterns/engineering/idea-file-executable-architecture/) | raw |
| PATTERN-036 | [Паттерн 36. «Интеллектуальная маршрутизация с самооценкой сложности» (Intelligent Model Routing)](patterns/engineering/intelligent-model-routing/) | raw |
| PATTERN-037 | [Паттерн 37. «Мультивекторный семантический индекс» (Multi-Vector Semantic Index)](patterns/engineering/multi-vector-semantic-index/) | raw |
| PATTERN-031 | [Паттерн 031. «Непрерывная ротация моделей без остановки конвейера» (Seamless Model Rotation in Vector Store)](patterns/engineering/seamless-model-rotation/) | raw |
| PATTERN-033 | [Паттерн 33. «Семантический веер запросов» (Semantic Query Fan-out)](patterns/engineering/semantic-query-fan-out/) | raw |
| PATTERN-040 | [Паттерн 40. «Пространственно-визуальная память интерфейсов» (Spatial-Visual UI Memory)](patterns/engineering/spatial-visual-ui-memory/) | raw |

## Индекс методов (16)

| METHOD-012 | [Агентный дебаггинг и алертинг](methods/agent-debugging-and-alerting/) | raw |
| METHOD-007 | [Контрольные точки агентного состояния (Agent State Checkpointing)](methods/agent-state-checkpointing/) | raw |
| METHOD-010 | [Стратегии чанкинга](methods/chunking-strategies/) | raw |
| METHOD-004 | [Принудительная шаблонизация с доказательным выводом (Constrained Templating with Evidence)](methods/constrained-templating-with-evidence/) | raw |
| METHOD-011 | [Контекстное окно и Prompt Cache](methods/context-window-and-prompt-cache/) | raw |
| METHOD-003 | [Канонизация данных под модель (Data Canonicalization for LLM)](methods/data-canonization-for-llm/) | raw |
| METHOD-006 | [Экономичный дисковый индекс для долгой памяти (Disk-Optimized Vector Index for Cold Memory)](methods/disk-optimized-vector-index-for-cold-memory/) | raw |
| METHOD-009 | [Конвейерная обработка и стратегии эмбеддинга (Data Processing Pipeline and Embedding Strategies)](methods/embedding-pipeline-and-strategies/) | raw |
| METHOD-014 | [Стандарт проведения экспериментов](methods/experiment-design-standard/) | raw |
| METHOD-016 | [Техники принудительного рассуждения (CoT, ToT, Self-Consistency)](methods/forced-reasoning-techniques/) | raw |
| METHOD-015 | [Управляемое исследование неизвестного незнания (Guided Exploration of Unknown Unknowns)](methods/guided-exploration-of-unknown-unknowns/) | raw |
| METHOD-002 | [Периметр безопасности на легковесных алгоритмах (Lightweight Security Perimeter)](methods/lightweight-security-perimeter/) | raw |
| METHOD-008 | [Многоуровневый контроль автоматических исправлений (Multi-layered Auto-Fix Review)](methods/multi-layered-auto-fix-review/) | raw |
| METHOD-013 | [Персистентность и эволюция правил](methods/rule-persistence-and-evolution/) | raw |
| METHOD-001 | [Сегрегация источников (Source Segregation)](methods/source-segregation/) | raw |
| METHOD-005 | [Структурно-осознанный препроцессинг артефактов (Structure-Aware Document Preprocessing)](methods/structure-aware-document-preprocessing/) | raw |

## Бэклог (12)

| BACKLOG-005 | [Прогрессия автономности агентов](backlog/agent-autonomy-progression/) | Observation |
| BACKLOG-009 | [Коллективная память агентов (Agent Collective Memory)](backlog/agent-collective-memory/) | Idea |
| BACKLOG-007 | [Агент в общем канале коммуникации](backlog/agent-in-shared-channel/) | Hypothesis |
| BACKLOG-002 | [Память агента как критический актив](backlog/agent-memory-as-critical-asset/) | Observation |
| BACKLOG-010 | [Самотестирование агента перед развёртыванием](backlog/agent-self-testing/) | Idea |
| BACKLOG-012 | [Белый список команд (Command Allowlist) — ограничение прав агента](backlog/command-allowlist/) | Candidate |
| BACKLOG-001 | [Диспетчер аналогов (Dispatcher-by-Goal)](backlog/dispatcher-by-goal/) | Hypothesis |
| BACKLOG-004 | [Парадигма «цель-результат» (Goal-Result Paradigm)](backlog/goal-result-paradigm/) | Hypothesis |
| BACKLOG-006 | [Зубчатый интеллект (Jagged Intelligence)](backlog/jagged-intelligence/) | Observation |
| BACKLOG-008 | [Spawn-Restrict-Collect](backlog/spawn-restrict-collect/) | Hypothesis |
| BACKLOG-003 | [Хуки жизненного цикла инструментов (Tool Lifecycle Hooks)](backlog/tool-lifecycle-hooks/) | Hypothesis |
| BACKLOG-011 | [Upstream-контур: от размытой цели к измеримым KPI (Коммуникатор → Постановщик задач)](backlog/upstream-loop/) | Idea |

## Антипаттерны (1)

| ANTIPATTERN-001 | [Антипаттерн. «Избыточная мощность модели» (Overpowered Model Anti-Pattern)](antipatterns/overpowered-model/) | applied |

## Приложения (1)

|  | [Приложение A. Каталог ролей агентной системы](appendices/agent-role-catalog/) | raw |

## Как участвовать

См. [CONTRIBUTING.md](CONTRIBUTING.md).

## Лицензия

MIT — см. [LICENSE](LICENSE).

## Контакты

- GitHub: [@boofer-obmena](https://github.com/boofer-obmena)
