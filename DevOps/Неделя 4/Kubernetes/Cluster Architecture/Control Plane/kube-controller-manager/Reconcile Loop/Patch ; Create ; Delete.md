---
sr-due: 2026-02-11
sr-interval: 80
sr-ease: 210
---

#sr-due 
- Контроллер вызывает `client-go` методы:
    - `Create()` — если нужно создать pod, replicaset, etc.
    - `Patch()` — обновить `.status` или `.spec`
    - `Delete()` — удалить неактуальные ресурсы
- Все изменения идут **через API Server**
- Иногда используется `UpdateStatus()` — для обновления `.status`, без перезаписи `.spec`

Контроллеры всегда используют Patch вместо Update, т.к. один объект могут менять несколько контроллеров и иначе они бы перетирали друг друга.

**типы patch**: 
JSON Merge Patch, Strategic Merge Patch (только для типов, описанных в Go), JSON Patch.
[[Patch ; Create ; Delete]]
[[Reconcile Loop (контроллерный цикл)]]