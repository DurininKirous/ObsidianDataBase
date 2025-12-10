---
sr-due: 2026-01-30
sr-interval: 77
sr-ease: 226
---

#sr-due 
StatefulSet - это объект для запуска stateful-приложений (состояние, уникальные идентификаторы, привязка к дискам)
В отличие от [[Obsidian Vault/Rebrain/Studying/DevOps/Неделя 4/Kubernetes/Cluster Architecture/Сущности/Deployment|Deployment]]:
- Pod'ы имеют стабильные имена (например, web-0, web-1, web-2)
- Каждый Pod может иметь свой PersistanceVolumeClaim
- Pod'ы запускаются и останавливаются по порядку
StatefulSet нужен для баз данных и сервисов, где каждый Pod должен быть "личностью"

Основные поля:
apiVersion: apps/v1
kind: StatefulSet
metadata:
  name: web
spec:
  replicas: 3
  selector:
    matchLabels:
      app: web
  serviceName: "web"
  template:
    metadata:
      labels:
        app: web
    spec:
      containers:
      - name: nginx
        image: nginx:1.27
  volumeClaimTemplates:
  - metadata:
      name: www
    spec:
      accessModes: [ "ReadWriteOnce" ]
      resources:
        requests:
          storage: 1Gi

- **replicas** — сколько Pod’ов нужно.
- **serviceName** — имя headless-сервиса, который даёт Pod’ам DNS-имена.
- **template** — шаблон Pod’а.
- **volumeClaimTemplates** — создаёт PVC для каждого Pod.

## Отличительные особенности
- Pod’ы именуются стабильно: `web-0`, `web-1`, `web-2`.
- У Pod’ов всегда **один и тот же PVC**, даже если Pod пересоздаётся.
- Контроллер запускает Pod’ы по порядку:
    - сначала `web-0`, потом `web-1`, потом `web-2`.
    - при удалении — в обратном порядке.
- Может работать с **PodDisruptionBudget**, чтобы не рушить кворум кластера (например, в базе данных).
- PVC «навсегда» остаются, даже если уменьшить `replicas`. Надо удалять вручную.
## Service и DNS
- Для StatefulSet почти всегда нужен **Headless Service** (`clusterIP: None`).
- Это даёт каждому Pod предсказуемое DNS-имя:
	- "pod-name"."service-name"."namespace".svc.cluster.local
	Пример: `db-0.db.default.svc.cluster.local`

PVC получают имена по схеме:
	volumeClaimTemplate.name-statefulset-name-ordinal
Например:
- PVC: `data-mysql-0`, `data-mysql-1`, `data-mysql-2`.
- Pod: `mysql-0`, `mysql-1`, `mysql-2`.

## Когда применять
- Базы данных (Postgres, MySQL, Cassandra).
- Kafka, Zookeeper, Redis Cluster.
- Любые системы, где нужен **persistent storage** и **уникальный Pod identity**
[[StatefulSet]]
[[Сущности]]