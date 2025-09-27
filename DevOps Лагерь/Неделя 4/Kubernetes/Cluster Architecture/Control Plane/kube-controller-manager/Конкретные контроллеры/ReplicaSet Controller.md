---
sr-due: 2025-09-28
sr-interval: 9
sr-ease: 210
---

#sr-due 

Задача:
	RepliceSet Controller следит, чтобы текущее количествао Pod'ов соответствовало spec.replicas
- Если Pod меньше -> создаёт новые
- Если Pod больше -> удаляет лишние
- Если Pod исчез -> восстанавливает

Как работает reconcile loop:
1. Informer следит за ReplicaSet и Pod
2. События попадают в WorkQueue
3. Контроллер создаёт ReplicaSet -> сверяет:
	- Сколько Pod'ов desired (spec.replicas)
	- Сколько реально есть (по `status`)
4. Если разница:
	- Создаёт/удаляет Pod через API-сервер
5. Обновляет .status у ReplicaSet 

Важные детали:
- Label Selector - главный критерий принадлежности подов
- Adoption & Orphaning:
	- Если в namespace есть Pod с нужным label, но без ownerReference -> ReplicaSet "усыновит" его
	- Если Pod потерял Label -> ReplicaSet перестаёт им управлять
- Status: контроллер обновляет .status, чтобы отразить реальное число Pod'ов 
[[ReplicaSet Controller]]
[[Конкретные контроллеры]]