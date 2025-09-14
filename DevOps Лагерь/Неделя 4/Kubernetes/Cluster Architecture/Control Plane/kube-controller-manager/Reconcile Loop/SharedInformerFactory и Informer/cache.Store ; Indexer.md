---
sr-due: 2025-09-14
sr-interval: 2
sr-ease: 230
---

#sr-due 
- Store - локальный in-memory кеш объектов
- При каждом изменении Reflector обновляет кеш
Контроллеры читают данные **только из кеша**, через `Lister`, а не напрямую из API
[[cache.Store ; Indexer]]
[[SharedInformerFactory и Informer]]