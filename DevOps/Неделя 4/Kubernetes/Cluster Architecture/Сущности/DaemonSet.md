---
sr-due: 2026-01-22
sr-interval: 74
sr-ease: 230
---

#sr-due 
Назначение:
	DaemonSet гарантирует, что на каждой ноде запущен ровно один описаныый Pod
	Используется для сервисов, которые должны быть рядом с инфраструктурой узла:
		агенты логирования
		агенты мониторинга
		сетевые плагины
Основные поля:
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

Особенности:
- Под разворачивается на каждой ноде
- Работает через nodeAffinity / tolerations: можно ограничить запуск только на части нод
- Если нода уходит из кластера -> под уходит вместе с ней
- Масштабирование через .spec.replicas отсутствует

Когда применять:
- Логгинг
- Мониторинг
- CNI плагины
- kube-proxy
[[DaemonSet]]
[[Сущности]]