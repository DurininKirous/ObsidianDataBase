---
sr-due: 2025-11-10
sr-interval: 32
sr-ease: 230
---

#sr-due 
**Pod Sandbox** = специальная «оболочка» для Pod, в которой запускаются все его контейнеры.
- Реализуется через **pause-контейнер** (infra container).
- Именно он создаёт и держит:
    - **сетевой namespace** Pod’а,
    - **IP-адрес**,
    - **hostname**,
    - cgroups,
    - DNS-настройки.
Все остальные контейнеры Pod подключаются к этому sandbox’у.

### Что будет, если sandbox упадёт
- kubelet увидит: Pod Sandbox умер.
- Убьёт все контейнеры Pod’а и пересоздаст новый sandbox (новый pause, новый IP).
- Pod рестартует заново.
[[Pod Sandbox]]
[[CRI]]