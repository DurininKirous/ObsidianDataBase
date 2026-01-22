---
sr-due: 2026-06-22
sr-interval: 165
sr-ease: 250
---

#sr-due 
kind: NetworkPolicy
apiVersion: networking.k8s.io/v1
metadata:
  name: default-deny-ingress
  namespace: app
spec:
  podSelector: {}          # выбрать все Pod'ы в namespace
  policyTypes: [Ingress]   # изоляция только по входу
  ingress: []              # пустой список => никто не может войти
Теперь Pod невидим снаружи, пока не напишешь allow
[[Default deny ingress]]
[[Базовые паттерны]]