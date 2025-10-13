---
sr-due: 2025-10-20
sr-interval: 7
sr-ease: 210
---

#sr-due 
apiVersion: networking.k8s.io/v1
kind: NetworkPolicy
metadata:
  name: restrict-egress
  namespace: app
spec:
  podSelector:
    matchLabels: { app: backend }
  policyTypes: [Egress]
  egress:
  # Разрешаем DNS
  - to:
    - namespaceSelector:
        matchLabels:
          kubernetes.io/metadata.name: kube-system
    ports:
    - { protocol: UDP, port: 53 }
    - { protocol: TCP, port: 53 }
  # Разрешаем БД по IP
  - to:
    - ipBlock:
        cidr: 10.20.30.40/32
    ports:
    - { protocol: TCP, port: 5432 }
Под не сможет «гулять» в интернет, только DNS + БД.
[[Egress только к DNS и БД]]
[[Базовые паттерны]]