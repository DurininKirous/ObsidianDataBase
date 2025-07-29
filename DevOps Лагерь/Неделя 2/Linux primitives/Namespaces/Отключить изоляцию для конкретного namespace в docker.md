---
sr-due: 2025-09-01
sr-interval: 35
sr-ease: 270
---

#sr-due 
Для этого достаточно запустить контейнер с параметрами типа $NS_NAME=host, например:
```
--pid=host
--net=host
--mnt=host
docker run --pid=host nginx -d
```
Опасно для безопасности, но полезно может быть для диагностики
[[Отключить изоляцию для конкретного namespace в docker]]
[[Namespaces]]