---
sr-due: 2025-10-17
sr-interval: 1
sr-ease: 230
---

#sr-due 
LB отправляет запрос на сервер с наименьшим количеством активных соединений

Server 1: 5 active connections
Server 2: 12 active connections <- перегружен
Server 3: 3 active connections <- сюда пойдёт запрос

Когда использовать: Запросы разной длительности (один выполняется 10ms, другеи 5s)
[[Least Connections]]
[[Алгоритмы балансировки]]