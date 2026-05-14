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
- **Глоссарий** — ключевые термины с определениями

## Быстрый старт

Выберите точку входа:

- **Я новичок в проектировании агентов** → Начните с [Prompt Chaining](patterns/functional/prompt-chaining/) и [Routing](patterns/functional/routing/)
- **Я проектирую мульти-агентную систему** → [Multi-Agent Collaboration](patterns/functional/multi-agent-collaboration/), [Inter-Agent Communication](patterns/functional/inter-agent-communication/)
- **Я отлаживаю надёжность агента** → [Reflection](patterns/functional/reflection/), [Exception Handling](patterns/engineering/exception-handling/), [Quality Gate Pipeline](patterns/engineering/quality-gate-pipeline/)
- **Мне нужна модель безопасности** → [Security Perimeter](patterns/functional/security-perimeter/)
- **Хочу увидеть полный индекс** → [Индекс паттернов](#индекс-паттернов), [Индекс методов](#индекс-методов), [Индекс философий](#индекс-философий)

## Как устроен PlayBook

Каждая сущность следует единой структуре: Проблема → Решение → Пример → Экспериментальная проверка → История применения.

Сущности перекрёстно связаны: паттерн ссылается на методы, которые использует, философии, которые воплощает, и источники, которые его сформировали.

Статусы:
- `raw` — первый черновик, требуется валидация
- `review` — на рецензировании
- `verified` — экспериментально подтверждён
- `stable` — проверен в бою

## Философии

| ID | Название | Статус |
|----|----------|--------|
| PHILOSOPHY-001 | [Первичность предметной области (DDD)](philosophy/domain-primacy/) | raw |
| PHILOSOPHY-002 | [Итеративное самоуглубление](philosophy/iterative-self-deepening/) | raw |
| PHILOSOPHY-003 | [Агентоцентричная архитектура](philosophy/agent-centric-architecture/) | raw |
| PHILOSOPHY-004 | [Семантическое версионирование контрактов](philosophy/semantic-contract-versioning/) | raw |
| PHILOSOPHY-005 | [Исполняемые спецификации](philosophy/executable-specifications/) | raw |
| PHILOSOPHY-006 | [Перекрёстная верификация источников](philosophy/cross-validation-of-sources/) | raw |
| PHILOSOPHY-007 | [Эмерджентное проектирование](philosophy/emergent-design/) | raw |

## Принципы

| ID | Название | Статус |
|----|----------|--------|
| PRINCIPLE-001–011 | [См. Индекс принципов](principles/) | raw |

## Индекс паттернов

### Функциональные паттерны

| ID | Название | Статус |
|----|----------|--------|
| PATTERN-001 | [Цепочка происхождения артефакта](patterns/functional/artifact-provenance-chain/) | raw |
| PATTERN-002 | [Prompt Chaining](patterns/functional/prompt-chaining/) | raw |
| PATTERN-003 | [Routing](patterns/functional/routing/) | raw |
| PATTERN-004 | [Parallelization](patterns/functional/parallelization/) | raw |
| PATTERN-005 | [Orchestrator Agents](patterns/functional/orchestrator-agents/) | raw |
| PATTERN-006 | [Evaluator-Optimizer](patterns/functional/evaluator-optimizer/) | raw |
| PATTERN-007 | [Reflection](patterns/functional/reflection/) | raw |
| PATTERN-008 | [Tool Augmentation](patterns/functional/tool-augmentation/) | raw |
| PATTERN-009 | [Multi-Agent Collaboration](patterns/functional/multi-agent-collaboration/) | raw |
| PATTERN-010 | [Inter-Agent Communication](patterns/functional/inter-agent-communication/) | raw |
| PATTERN-011–029 | [См. Функциональные паттерны](patterns/functional/) | raw |
| PATTERN-043–050 | [См. Продвинутые паттерны](patterns/functional/) | raw |

### Инженерные паттерны

| ID | Название | Статус |
|----|----------|--------|
| PATTERN-030–042 | [См. Инженерные паттерны](patterns/engineering/) | raw |
| PATTERN-051 | [Security Hardening](patterns/engineering/) | raw |

## Индекс методов

| ID | Название | Статус |
|----|----------|--------|
| METHOD-001–016 | [См. Методы](methods/) | raw |

## Как участвовать

См. [CONTRIBUTING.md](CONTRIBUTING.md).

## Лицензия

MIT — см. [LICENSE](LICENSE).

## Контакты

- GitHub: [@boofer-obmena](https://github.com/boofer-obmena)
