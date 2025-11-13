---
sr-due: 2026-01-19
sr-interval: 71
sr-ease: 230
---

#sr-due 
Когда kubelet запускает Pod, ему нужно:
- создать сетевой namespace
- назначить IP-адрес
- прописать маршруты и DNS
kubelet сам этого не делает, он делегирует задачу CNI-плагину
[[CNI]]
[[kubelet]]