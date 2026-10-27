---
description: Read-only review of scoped BSL changes and architecture decisions, with evidence, severity, confidence, and residual-risk reporting
alwaysApply: false
category: quality
---

# Ревью кода и архитектуры

Применять только при явном запросе на ревью. До начала получить точный scope: diff, список файлов или готовое архитектурное решение. Если scope отсутствует или неоднозначен, уточнить его; не угадывать состав изменений по рабочему дереву.

## Маршрутизация

- Ревью кода или diff — прочитать `.opencode/rules/source-search.md`, `.opencode/rules/coding-standards.md`, `.opencode/rules/verification.md` и дополнительные правила по виду затронутых артефактов согласно корневому `AGENTS.md`.
- Ревью готового архитектурного решения — прочитать `.opencode/rules/architecture.md`; `.opencode/rules/source-search.md` и правила артефактов загружать только для проверки решения по фактическим исходникам.
- Если scope совмещает оба вида ревью, объединить маршруты. Остальные правила не загружать.

## Ограничения

- Работать только для чтения и ничего не изменять в рамках ревью.
- Инструменты использовать только для подтверждения фактов.
- Для кода проверять функциональные ошибки, контексты, `NULL`/`Неопределено`, транзакции, безопасность, производительность и регрессии API.
- Для архитектуры проверять границы компонентов, модель данных, интеграции, права, конкурентность, совместимость, тестируемость и rollback.
- Не включать предположения с низкой уверенностью в findings; перечислять их как проверочные вопросы или остаточные риски.

## Формат результата

```markdown
## Review Result
**Scope:** ...
**Status:** APPROVE / CONCERNS / BLOCK

### critical|major|minor — Заголовок
**Location:** `path:line` или компонент
**Confidence:** high/medium
**Evidence:** ...
**Consequence:** ...
**Fix / next check:** ...

## Residual risk
- ...
```
