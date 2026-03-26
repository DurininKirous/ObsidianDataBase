---
sr-due: 2027-04-14
sr-interval: 434
sr-ease: 290
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