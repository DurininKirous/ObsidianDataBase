---
created: 2026-01-17 11:18
tags:
  - status/seed
  - type/concept
  - domain/linux
  - sr-due
sr-due: 2026-06-20
sr-interval: 154
sr-ease: 230
---
### 💡 The What
*Что это?*
У kubelet есть разные точки сбора разных метрик, ниже описание основных

### ⚙️ The Why & How
*Инженерная суть. Механика. Зачем это нужно?*
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
    - `kubelet_pod_worker_duration_seconds` (латентность [[Что такое SyncPod Loop]]).
    - `kubelet_running_pods`.
    - `kubelet_volume_stats_*`.
    - `kubelet_prober_*` (результаты [[Probe]]).
    - `container_runtime_operations_total` (вызовы [[CRI]]).

---
### ⚔️ VS / Trade-offs
*С чем сравнить? Плюсы/Минусы.*
- **VS [[...]]**: 
- **Trade-off**: 


---
### 🔗 Connections
- **Родитель**: [[kubelet]]
- **Влияет на**: [[...]]
- **Инсайт**: 
