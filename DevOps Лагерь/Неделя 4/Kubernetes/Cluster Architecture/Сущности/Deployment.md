---
sr-due: 2025-09-15
sr-interval: 2
sr-ease: 210
---

#sr-due 
Deployment - это объект для управления жизненным циклом приложения:
- создаёт и масштабирует поды
- обновляет поды на новую версию без простоя
- позволяет откатываться на предыдущие версии

Основные поля:
apiVersion: apps/v1
kind: Deployment
metadata:
  name: myapp
spec:
  replicas: 3
  selector:
    matchLabels:
      app: myapp
  strategy:
    type: RollingUpdate
    rollingUpdate:
      maxUnavailable: 1
      maxSurge: 1
  template:
    metadata:
      labels:
        app: myapp
    spec:
      containers:
      - name: nginx
        image: nginx:1.27

**strategy** — стратегия обновления:
- `Recreate`: удалить все старые Pod’ы, потом создать новые.
##- `RollingUpdate`: постепенно обновлять (по `maxUnavailable` и `maxSurge`).

### Когда применять
- Stateless приложения (web, api, worker).
- Когда важен **контроль версий** (deployment → update → rollback).
- Когда нужно **масштабирование** (ручное или через HPA).
[[DevOps Лагерь/Неделя 4/Kubernetes/Cluster Architecture/Сущности/Deployment|Deployment]]
[[Сущности]]