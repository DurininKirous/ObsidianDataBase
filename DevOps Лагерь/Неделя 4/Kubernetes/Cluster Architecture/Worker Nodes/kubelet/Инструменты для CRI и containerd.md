---
sr-due: 2025-10-07
sr-interval: 12
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