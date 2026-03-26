---
created: 2026-02-01 12:00
tags:
  - status/seed
  - type/concept
  - domain/linux
  - sr-due
sr-due: 2026-08-02
sr-interval: 182
sr-ease: 230
---
### 💡 The What
*Что это?*
DaemonSet гарантирует, что на каждой ноде запущен ровно один описаныый Pod


### ⚙️ The Why & How
*Инженерная суть. Механика. Зачем это нужно?*
Используется для сервисов, которые должны быть рядом с инфраструктурой узла:
	агенты логирования
	агенты мониторинга
	сетевые плагины
Основные поля:
```
apiVersion: apps/v1
kind: DaemonSet
metadata:
  name: node-exporter
spec:
  selector:
    matchLabels:
      app: node-exporter
  template:
    metadata:
      labels:
        app: node-exporter
    spec:
      containers:
      - name: exporter
        image: prom/node-exporter:latest
```

Особенности:
- Под разворачивается на каждой ноде
- Работает через [[Affinity and AntiAffinity]] / [[Taints and Tolerations]]: можно ограничить запуск только на части нод
- Если нода уходит из кластера -> под уходит вместе с ней
- Масштабирование через .spec.replicas отсутствует

Когда применять:
- Логгинг
- Мониторинг
- CNI плагины
- kube-proxy

---
### 🔗 Connections
- **Родитель**: [[Сущности]], [[DaemonSet в k8s]]
