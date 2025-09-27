---
sr-due: 2025-10-05
sr-interval: 12
sr-ease: 230
---

#sr-due 
1. Основная задача
	1. Следить за объектами CronJob
	2. По расписанию запускать новые Job
	3. Управлять историей старых Job
2. Как работает reconcile loop
	1. Informer следит за CronJob
	2. Контроллер проверяет:
		1. spec.schedule
		2. Когда в последний раз запускался Job (status.lastScheduleTime)
	3. Если время запуска наступило:
		1. Создаёт новый Job на основе .spec.jobTemplate
	4. Проверяет ограничения:
		1. concurrencyPolicy (Allow, Forbid, Replace): решает, запускать ли новый Job, если старый ещё не завершён
		2. startingDeadlineSeconds: если пропустили запуск, можно догнать в пределах таймаута
	5. Управляет историей:
		1. Удаляет старые Job по successfulJobsHistoryLimit и failedJobsHistoryLimit
	6. Обновляет .status.lastScheduleTime
3. Важные особенности
	1. CronJon Controller не запускает Pod напрямую - он всегда создаёт Job
	2. При падении контроллера запуска может не быть -> startDeadlineSeconds помогает "догнать"
	3. Если `concurencyPolicy=Replace` -> старый Job удаляется, новый создаётся
4. Пример сценариев
	1. `schedule: "*/5 * * * *"` → каждые 5 минут CronJob Controller создаёт новый Job.
	2. Если `concurrencyPolicy=Forbid` → Job не стартует, пока предыдущий не закончен.
	3. Если `startingDeadlineSeconds=200` → при лаге контроллер может запустить пропущенный Job задним числом.

[[CronJob Controller]]
[[CronJob]]
[[Конкретные контроллеры]]