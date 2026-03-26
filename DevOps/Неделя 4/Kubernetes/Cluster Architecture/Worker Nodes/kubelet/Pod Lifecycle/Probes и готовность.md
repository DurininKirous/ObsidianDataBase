---
sr-due: 2026-08-16
sr-interval: 188
sr-ease: 230
---

#sr-due 
- startupProbe: даёт приложению "проснуться". Пока не "ок", liveness/readiness не активны
- livenessProbe: провал -> kubelet рестартует контейнер
- readinessProbe: провал -> Pod исключают из Endpoints, но Pod остаётся running
Conditions:
- Initialized (init-контейнеры прошли)
- Ready (Pod готов принимать трафик)
- ContainersReady (Все контейнеры готовы)
- PodScheduled
[[Probes и готовность]]
[[Pod Lifecycle]]