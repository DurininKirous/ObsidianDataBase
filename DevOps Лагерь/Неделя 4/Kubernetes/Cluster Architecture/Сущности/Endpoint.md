---
sr-due: 2025-10-01
sr-interval: 7
sr-ease: 230
---

#sr-due 
## Что это
- В Kubernetes **Service сам по себе не знает**, куда слать трафик.
- Для этого есть объект **Endpoints**: список **Pod IP + targetPort**, которые соответствуют Service.
Пример:
apiVersion: v1
kind: Endpoints
metadata:
  name: my-service
subsets:
- addresses:
  - ip: 10.244.1.5
  - ip: 10.244.2.7
  ports:
  - port: 8080
Этот объект автоматически создаёт и обновляет **Endpoint Controller**, который следит за Pod’ами, подходящими под `selector` сервиса.
[[Endpoint]]
[[Сущности]]