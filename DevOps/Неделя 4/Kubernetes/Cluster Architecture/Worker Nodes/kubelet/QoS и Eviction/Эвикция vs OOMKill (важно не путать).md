---
sr-due: 2026-01-30
sr-interval: 77
sr-ease: 230
---

#sr-due 
- **OOMKill внутри cgroup** (превышен `memory.limit` контейнера):
    - Контейнер завершится `Reason=OOMKilled`, Pod **останется** на ноде и может быть перезапущен (в зависимости от `restartPolicy`).
    - Это **НЕ** эвикция, kubelet Pod не удалял, просто kernel убил процесс.
- **Evicted** (давление на ноде):
    - kubelet **удаляет** Pod целиком (graceful: SIGTERM → `terminationGracePeriodSeconds` → SIGKILL),
    - контроллер (ReplicaSet/Deployment/…) пересоздаст его **на другой ноде** (если есть куда).

Кратко: **OOMKilled** — локальная проблема контейнера; **Evicted** — системная нехватка на ноде.
[[Эвикция vs OOMKill (важно не путать)]]
[[QoS и Eviction]]