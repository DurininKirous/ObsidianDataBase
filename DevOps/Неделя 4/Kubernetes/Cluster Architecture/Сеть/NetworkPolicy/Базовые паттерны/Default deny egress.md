---
sr-due: 2025-12-24
sr-interval: 58
sr-ease: 250
---

#sr-due 
kind: NetworkPolicy
apiVersion: networking.k8s.io/v1
metadata:
  name: default-deny-egress
  namespace: app
spec:
  podSelector: {}
  policyTypes: [Egress]
  egress: []
Полезно для ограничений "в интернет не ходим", кроме явных исключений
[[Default deny egress]]
[[Базовые паттерны]]