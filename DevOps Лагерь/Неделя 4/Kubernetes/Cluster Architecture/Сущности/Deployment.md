---
sr-due: 2025-09-27
sr-interval: 8
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
- `RollingUpdate`: постепенно обновлять (по `maxUnavailable` и `maxSurge`).
- `maxUnavailable` → сколько Pod’ов можно одновременно «положить» при обновлении,
- `maxSurge` → сколько новых Pod’ов можно поднять сверх желаемого числа.
### Когда применять
- Stateless приложения (web, api, worker).
- Когда важен **контроль версий** (deployment → update → rollback).
- Когда нужно **масштабирование** (ручное или через HPA).

## Rollback
- Команда:
	kubectl rollout undo deployment my-deploy
Kubernetes хранит историю ReplicaSet и может откатиться на предыдущую версию.

## Canary / Blue-Green (на базе Deployment)
- **Canary**: несколько Pod’ов с новой версией → тестируем → потом раскатываем дальше. Обычно через несколько Deployment + Service.
- **Blue-Green**: 2 Deployment (старый и новый), Service переключается на новый целиком.
[[DevOps Лагерь/Неделя 4/Kubernetes/Cluster Architecture/Сущности/Deployment|Deployment]]
[[Сущности]]