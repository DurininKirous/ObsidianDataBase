---
sr-due: 2026-02-24
sr-interval: 84
sr-ease: 210
---

#sr-due 
- **Что делает:**
    - Удаляет orphaned объекты по `ownerReferences`.
    - Работает в связке с Finalizers и Deletion propagation.
- **Зачем:** автоматическая чистка “сиротских” объектов (например, ReplicaSet после удаления Deployment).
[[GarbageCollector]]
[[Конкретные контроллеры]]