---
sr-due: 2026-05-10
sr-interval: 122
sr-ease: 210
---

#sr-due 
- Store - локальный in-memory кеш объектов
- При каждом изменении Reflector обновляет кеш
Контроллеры читают данные **только из кеша**, через `Lister`, а не напрямую из API
[[cache.Store ; Indexer]]
[[SharedInformerFactory и Informer]]