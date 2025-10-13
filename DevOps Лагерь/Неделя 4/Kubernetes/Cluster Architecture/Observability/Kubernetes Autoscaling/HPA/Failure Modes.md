---
sr-due: 2025-10-14
sr-interval: 1
sr-ease: 230
---

#sr-due 
- Metrics not available: HPA пропускает цикл, пишет Event `failed to get CPU utilization`
- Resource busy: метрики устарели -> использует последнее известное значение
- Conflict with rollout: Deployment busy Updating -> HPA ждёт .status.updatedReplicas == spec.replicas
[[Failure Modes]]
[[HPA]]