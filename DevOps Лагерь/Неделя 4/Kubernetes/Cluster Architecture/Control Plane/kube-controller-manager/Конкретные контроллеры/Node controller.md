---
sr-due: 2025-10-08
sr-interval: 14
sr-ease: 230
---

#sr-due 

1. Основная задача
	1. Следить за состоянием нод
	2. Обновлять статус
	3. Делать eviction Pod'ов с нод, которые недоступны
	4. Управлять taints
2. Как работает
	1. Heartbeat
		1. kubelet на каждой ноде шлёт "пульс" API-серверу
		2. Node Controller мониторит эти heartbeats
	2. Проверка статуса
		1. Если hearbeat долго не приходит (`node-monitor-grace-period`, по умолчанию 40с) -> нода помечается как `NotReady`
	3. Eviction Pod'ов
		1. Если нода в NotReady слишком долго (`pod-eviction-timeout`, по умолчанию, 5 минут)
		2. Pod'ы пересоздаются на других нодах
	4. Управление taints
		1. Когда нода NotReady -> ставится taint (node.kubernetes.io/unreachable)
		2. Pod'ы, которые не имеют toleration к этому taint, будут вытеснены
3. Важные параметры
	1. --node-monitor-period (по умолчанию 5с) -> как часто проверять ноды
	2. --node-monitor-grace-period (пр умолчанию 40с) -> сколько ждлать без heartbeat, чтобы признать ноду NotReady
	3. --pod-eviction-timeout (по умолчанию 5м) -> через сколько минут после NotReady начать выселять Pod'ы
4. Пример сценариев
	1. kubelet умер -> Node Controller через 40с пометит ноду NotReady
	2. Если за 5 минут нода не вернулась -> Pod'ы будут эвакуированы и пересозданы на других нодах
	3. Если нода восстановилась до истечения `pod-eviction-timeout` -> Pod'ы остаются, эвакуация не происходит
[[DevOps Лагерь/Неделя 4/Kubernetes/Cluster Architecture/Worker Nodes/Node Controller|Node Controller]]
[[Node]]
[[Конкретные контроллеры]]