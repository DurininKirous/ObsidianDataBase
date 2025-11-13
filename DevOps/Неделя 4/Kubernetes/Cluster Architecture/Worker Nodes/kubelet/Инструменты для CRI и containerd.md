---
sr-due: 2026-01-16
sr-interval: 68
sr-ease: 230
---

#sr-due 
### список Pod Sandbox-ов (pause контейнеры)
crictl pods

### список контейнеров
crictl ps -a

### статус Pod’а
crictl inspectp <POD_ID>

### статус контейнера
crictl inspect <CONTAINER_ID>

### логи контейнера
crictl logs <CONTAINER_ID>

### пулл образа
crictl pull nginx:latest

[[Инструменты для CRI и containerd]]
[[Worker Nodes]]