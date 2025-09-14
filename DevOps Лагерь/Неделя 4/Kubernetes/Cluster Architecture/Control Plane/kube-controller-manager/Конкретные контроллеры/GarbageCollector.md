#sr-due 
- **Что делает:**
    - Удаляет orphaned объекты по `ownerReferences`.
    - Работает в связке с Finalizers и Deletion propagation.
- **Зачем:** автоматическая чистка “сиротских” объектов (например, ReplicaSet после удаления Deployment).
[[GarbageCollector]]
[[Конкретные контроллеры]]