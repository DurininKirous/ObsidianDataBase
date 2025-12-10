---
sr-due: 2026-02-14
sr-interval: 81
sr-ease: 206
---

#sr-due 
Проверяет, что ресурс соответствует OpenAPI-схеме.
После mutation и до записи в etcd:
- проверяется required, enum, type, pattern, maximum, minimum
- работает по OpenAPI-схеме ресурса
Ошибки дают `422 Unprocessable Entity` при `kubectl apply`
Как:
- Проверяет поля на тип, required, enum, min/max
- Работает после `mutating admission` перед `etcd`
Без него:
- Можно было бы засунуть в API мусор (невалидные поля, ошибки)
- Возможны сбои в клиентах, watch, и прочих consumers API
[[Object Schema Validation]]
[[Структура внутри apiserver]]