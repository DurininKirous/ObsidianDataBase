---
sr-due: 2025-11-12
sr-interval: 34
sr-ease: 230
---

#sr-due 
- kubelet подписывается (watch) на Pod'ы с spec.nodeName = "эта нода"
- Регулярно обновляет статус ноды: Node.status.conditions и объект Lease (heartbeat)
- Для каждого Pod'а пишет статус через подресурс /status
[[Как kubelet общается с API-сервером]]
[[kubelet]]