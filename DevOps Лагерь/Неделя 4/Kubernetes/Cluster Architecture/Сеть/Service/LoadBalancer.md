---
sr-due: 2025-10-18
sr-interval: 17
sr-ease: 230
---

#sr-due 
- В облаках создаётся внешний LB, который шлёт трафик на NodePort'ы
- `externalTrafficPolicy` работает так же, как и для NodePort.
- Часто есть **health-checks** LB, которые проверяют локальные endpoints на ноде.
[[LoadBalancer]]
[[Service]]