#sr-due 
Назначение:
	Cronjob запускает Job по расписанию, похож на `cron` в Linux
		Можно описать задачу, которая должна стартовать регулярно
		CronJob сам создаёт Job-объекты в нужное время
		
Основные поля:
apiVersion: batch/v1
kind: CronJob
metadata:
  name: hello
spec:
  schedule: "*/5 * * * *"   # каждые 5 минут
  jobTemplate:
    spec:
      template:
        spec:
          containers:
          - name: hello
            image: busybox
            args:
            - /bin/sh
            - -c
            - date; echo Hello from Kubernetes!
          restartPolicy: OnFailure
		  
- **schedule** — расписание в формате cron.
- **jobTemplate** — шаблон Job, который будет запускаться.
- **concurrencyPolicy**:
    - `Allow` (по умолчанию) → новые Job’ы могут запускаться, даже если старые ещё не завершились.
    - `Forbid` → если предыдущая задача не закончилась, новая не стартует.
    - `Replace` → новая замещает старую.
- **startingDeadlineSeconds** — таймаут: если Job должен был начаться, но kube-controller-manager не успел (например, контроллер был недоступен), его можно запустить позже в пределах этого времени.
- **successfulJobsHistoryLimit** / **failedJobsHistoryLimit** — сколько старых Job хранить.

Применение:
- Ежедневные бэкапы
- Регулярные отчёты
- Очистка временных файлов
- Запуск maintenance-скриптов
[[CronJob]]
[[Сущности]]