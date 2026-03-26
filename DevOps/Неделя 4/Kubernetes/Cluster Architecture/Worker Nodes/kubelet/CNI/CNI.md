---
sr-due: 2026-08-05
sr-interval: 182
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