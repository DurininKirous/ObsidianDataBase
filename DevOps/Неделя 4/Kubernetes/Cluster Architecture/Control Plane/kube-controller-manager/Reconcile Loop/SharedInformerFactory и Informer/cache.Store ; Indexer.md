---
sr-due: 2025-12-26
sr-interval: 53
sr-ease: 210
---

#sr-due 
- Store - локальный in-memory кеш объектов
- При каждом изменении Reflector обновляет кеш
Контроллеры читают данные **только из кеша**, через `Lister`, а не напрямую из API
[[cache.Store ; Indexer]]
[[SharedInformerFactory и Informer]]