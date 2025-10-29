---
sr-due: 2025-11-11
sr-interval: 30
sr-ease: 230
---

#sr-due 
Он связывает CoreDNS и Kubernetes API.
- Перехватывает запросы в зоне `cluster.local`.
- Для Service → возвращает **ClusterIP** (или Pod IP, если headless).
- Для Pod (если разрешено) → возвращает его IP.
- Работает вместе с EndpointSlice — исключает Pod’ы, у которых readiness=false.
[[Главный плагин - kubernetes]]
[[CoreDNS]]