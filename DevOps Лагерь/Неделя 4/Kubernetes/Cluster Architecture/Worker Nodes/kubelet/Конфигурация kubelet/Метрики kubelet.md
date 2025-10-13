---
sr-due: 2025-11-07
sr-interval: 29
sr-ease: 230
---

#sr-due 
## 1. Endpoints
- `:10255` (insecure, отключён по умолчанию) → `/stats/summary`.
- `:10248` → `healthz` (`/healthz`, `/healthz/log`, `/healthz/ping`).
- `:10250` (secured) → метрики и управление (kubectl exec/logs).
- `:10255` в проде обычно закрыт, используют через API-сервер (metrics-server).

## 2. Summary API
- kubelet собирает статистику из **cAdvisor**.
- Доступ: `/stats/summary`.
- Содержит: CPU, память, файловая система, usage по Pod и контейнеру.
- Используется metrics-server (kubectl top pod/node).

## 3. Prometheus-метрики
- kubelet экспонирует `/metrics` (Prometheus формат).
- Основные группы:
    - `kubelet_pod_worker_duration_seconds` (латентность SyncPod).
    - `kubelet_running_pods`.
    - `kubelet_volume_stats_*`.
    - `kubelet_prober_*` (результаты проб).
    - `container_runtime_operations_total` (вызовы CRI).
[[Метрики kubelet]]
[[Конфигурация kubelet]]