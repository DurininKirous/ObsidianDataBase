---
sr-due: 2025-10-17
sr-interval: 19
sr-ease: 210
---

#sr-due 
Когда удаляешь владельца (owner, у которого есть dependents по `ownerReferences`):
- Foreground: сначала удаляются зависимые, и только затем удаляет owner. Гарантирует "чистое дерево"
- Background: owner удаляет сразу,  а GC удаляет зависимых в фоне
- Orphan: owner удаляют, зависимые сохраняются

Это управляется флагом **propagationPolicy** (или устаревшим `--cascade`).
- **Namespace deletion** → всегда Foreground (иначе могли бы остаться объекты в “висячем” состоянии).
- **Обычное удаление ресурсов** (Deployment, ReplicaSet, etc.) → Background (по умолчанию).
- **Orphan** → только вручную (`--cascade=orphan` / `propagationPolicy: Orphan`).
[[Deletion propagation]]
[[Finalizers]]