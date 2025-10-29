---
sr-due: 2025-11-08
sr-interval: 30
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