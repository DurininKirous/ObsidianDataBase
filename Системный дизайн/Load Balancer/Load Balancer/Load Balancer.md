---
sr-due: 2025-10-23
sr-interval: 4
sr-ease: 224
---

#sr-due 
### Зачем нужен Load Balancer?
Проблема без load balancer:
	Client -> Single Server (SPOF!)
- Если сервер упал - всё упало
- Один сервер не справляется с нагрузкой
- Невозможно обновление без downtime

Решение с LB:       -> Server 1
				   |
Client -> LB --------> Server 2
				   |
				   -> Server 3

Что даёт LB:
- Распределение нагрузки между серверами
- Отказоустойчивость (Если Server 2 упал,  LB перестаёт слать туда запросы)
- Zero-downtime deployment (обновляем по ондому серверу)
- Horizontal scaling  (добавляем новые серверы динамически)
[[Load Balancer]]
[[Системный дизайн]]