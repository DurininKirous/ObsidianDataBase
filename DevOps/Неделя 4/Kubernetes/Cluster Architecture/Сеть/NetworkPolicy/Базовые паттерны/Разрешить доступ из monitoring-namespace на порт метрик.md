---
sr-due: 2026-06-23
sr-interval: 166
sr-ease: 250
---

#sr-due 
kind: NetworkPolicy
apiVersion: networking.k8s.io/v1
metadata:
  name: allow-monitoring
  namespace: app
spec:
  podSelector: {}   # все Pod'ы в ns app
  policyTypes: [Ingress]
  ingress:
  - from:
    - namespaceSelector:
        matchLabels:
          kubernetes.io/metadata.name: monitoring
    ports:
    - port: 9100
      protocol: TCP
Теперь prometheus из monitoring ns может снимать метрики
[[Разрешить доступ из monitoring-namespace на порт метрик]]
[[Базовые паттерны]]