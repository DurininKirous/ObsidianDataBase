---
created: 2026-02-01 11:11
tags:
  - status/seed
  - type/concept
  - domain/linux
  - sr-due
sr-due: 2026-07-09
sr-interval: 158
sr-ease: 210
---
### 💡 The What
*Что это?*
Есть набор ограничений, которые влияют на выбор ноды для пода в kube-scheduler в k8s

### ⚙️ The Why & How
*Инженерная суть. Механика. Зачем это нужно?*

| Тип ограничения      | Как задаётся                             |
| -------------------- | ---------------------------------------- |
| `NodeSelector`       | `pod.spec.nodeSelector`                  |
| `NodeAffinity`       | `preferredDuringScheduling...`           |
| `Taints/Tolerations` | Node таинты → pod toleration             |
| `PodAffinity`        | affinity к другим pod'ам (напр. sidecar) |
| `TopologySpread`     | распределение по зоне, rack и т.д.       |
| `Resource Requests`  | CPU, memory                              |

---
### 🔗 Connections
- **Родитель**: [[kube-scheduler]], [[Ограничения, которые влияют на выбор Node для Pod в k8s]]
- **Влияет на**: [[Алгоритм 2 фазы]]
