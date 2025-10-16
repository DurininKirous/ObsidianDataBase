---
sr-due: 2025-10-21
sr-interval: 5
sr-ease: 230
---

#sr-due 
- Metrics not available: HPA пропускает цикл, пишет Event `failed to get CPU utilization`
- Resource busy: метрики устарели -> использует последнее известное значение
- Conflict with rollout: Deployment busy Updating -> HPA ждёт .status.updatedReplicas == spec.replicas
[[Failure Modes]]
[[HPA]]