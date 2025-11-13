---
sr-due: 2026-04-05
sr-interval: 147
sr-ease: 230
---

#sr-due 
- Объединяет контейнеры с разных хостов
- Использует **VXLAN** (UDP туннель), если настроен `docker swarm`
- Контейнеры общаются по имени
- Требует discovery: etcd, consul, или built-in swarm
[[overlay]]
[[Типы сетей в Docker]]