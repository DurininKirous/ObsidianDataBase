---
sr-due: 2025-10-22
sr-interval: 19
sr-ease: 210
---

#sr-due 
- **Что делает:**
    - Удаляет orphaned объекты по `ownerReferences`.
    - Работает в связке с Finalizers и Deletion propagation.
- **Зачем:** автоматическая чистка “сиротских” объектов (например, ReplicaSet после удаления Deployment).
[[GarbageCollector]]
[[Конкретные контроллеры]]