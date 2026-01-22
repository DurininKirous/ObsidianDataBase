---
sr-due: 2026-06-23
sr-interval: 166
sr-ease: 250
---

#sr-due 
kind: NetworkPolicy
apiVersion: networking.k8s.io/v1
metadata:
  name: allow-frontend-to-backend
  namespace: app
spec:
  podSelector:
    matchLabels: { app: backend }   # применяем к backend Pod'ам
  policyTypes: [Ingress]
  ingress:
  - from:
    - podSelector: { matchLabels: { app: frontend } }
    ports:
    - protocol: TCP
      port: 80
Теперь backend принимает запросы от frontend только по 80/TCP
[[Разрешить только frontend -> backend 80]]
[[Базовые паттерны]]