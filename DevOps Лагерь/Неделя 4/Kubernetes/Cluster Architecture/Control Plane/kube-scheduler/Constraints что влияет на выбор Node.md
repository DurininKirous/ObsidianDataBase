---
sr-due: 2025-09-15
sr-interval: 2
sr-ease: 210
---

#sr-due 

| Тип ограничения      | Как задаётся                             |
| -------------------- | ---------------------------------------- |
| `NodeSelector`       | `pod.spec.nodeSelector`                  |
| `NodeAffinity`       | `preferredDuringScheduling...`           |
| `Taints/Tolerations` | Node таинты → pod toleration             |
| `PodAffinity`        | affinity к другим pod'ам (напр. sidecar) |
| `TopologySpread`     | распределение по зоне, rack и т.д.       |
| `Resource Requests`  | CPU, memory                              |
[[Constraints что влияет на выбор Node]]
[[kube-scheduler]]