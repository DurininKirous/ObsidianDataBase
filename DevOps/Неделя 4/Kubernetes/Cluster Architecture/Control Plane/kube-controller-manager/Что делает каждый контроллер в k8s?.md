---
created: 2026-01-29 09:15
tags:
  - status/seed
  - type/concept
  - domain/k8s
  - sr-due
sr-due: 2026-07-04
sr-interval: 156
sr-ease: 210
---
### ⚙️ The Why & How
*Инженерная суть. Механика. Зачем это нужно?*

| Контроллер                                                                                        | Назначение                                      |
| ------------------------------------------------------------------------------------------------- | ----------------------------------------------- |
| [[ReplicaSet Controller]]                                                                         | Следит, чтобы было N pod’ов в нужных состояниях |
| [[Deployment Controller]]                                                                         | Обновление pod’ов через RS, rollout, rollback   |
| [[StatefulSet Controller]]                                                                        | Identity pod’ов + PVC                           |
| [[DaemonSet Controller]]                                                                          | Один pod на каждую node                         |
| [[Job Controller]] / [[CronJob Controller]]                                                       | Разовые / периодические задачи                  |
| [[DevOps/Неделя 4/Kubernetes/Cluster Architecture/Worker Nodes/Node Controller\|Node Controller]] | Слежение за `NotReady`, выставление `taints`    |
| [[ServiceAccount Controller]]                                                                     | Автоматическое создание SA                      |
| [[Endpoints Controller]]                                                                          | Сопоставление pod’ов и service                  |
| [[GarbageCollector]]                                                                              | Очистка orphaned объектов                       |
| [[TTLAfterFinished Controller]]                                                                   | Удаление завершённых Job                        |

---
### 🔗 Connections
- **Родитель**: [[kube-controller-manager]]
