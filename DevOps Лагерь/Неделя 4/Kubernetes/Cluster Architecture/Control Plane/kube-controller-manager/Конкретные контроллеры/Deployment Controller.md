---
sr-due: 2025-09-14
sr-interval: 1
sr-ease: 190
---

#sr-due 
1. Задача
	1. Управляет ReplicaSet'ами, создаваемыми Deployment
	2. Обеспечивает корректный Rollout
	3. Хранит историю версий 
	4. Поддерживает масштабирование и rollback
2. Как работает reconcile loop
	1. Informer следит за Deployment'ами и их ReplicaSet'ами
	2. События летят в WorkQueue
	3. Контроллер достаёт Deployment и сверяет:
		1. spec.replicas - сколько pod'ов должно быть
		2. spec.template - какой шаблон pod'ов должен быть
		3. status у deployment 
	4. Проверяет: изменился ли pod template
		1. Если да: создаёт новый ReplicaSet с новым pod template
		2. Настраивает rollout стратегией
	5. Управляет количеством pod'ов в старом и новом ReplicaSet, пока не достигентся desired state
	6. Обновляет .status у Deployment:
		1. updatedReplicas - новые pod'ы с актуальным шаблоном
		2. availableReplicas - pod'ы, которые прошли readiness
		3. observedGeneration - до какой версии Deployment он дошёл
3. Поддержка rollback
	1. Deployment хранит несколько старых ReplicaSet
	2. Если новый rollout неудачный -> можно откатиться к старом с помощью ReplicaSet
	3. Контроллер просто масштабирует нужный ReplicaSet до нужного числа Pod'ов
4. Key нюансы
	1. Pause/Resume: можно остановить rollout и потом продолжить
	2. maxUnavailable / maxSurge: управляет скоростью rollingUpdate
	3. ProgressingDeadlineSeconds: ограничивает время ожидания успешного rollout
	4. Recreate стратегия: удаляет все pod'ы сразу, потом создаёт новые

[[Deployment Controller]]
[[DevOps Лагерь/Неделя 4/Kubernetes/Cluster Architecture/Сущности/Deployment|Deployment]]
[[Конкретные контроллеры]]