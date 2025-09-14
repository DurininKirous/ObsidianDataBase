#sr-due 
Job - это объект для выполнения одноразовой задачи до завершения.
В отличие от Deployment/ReplicaSet, Job гарантирует, что Pod будет выполнен N раз успешно.

Используется для:
	Миграций БД
	Бэкапов
	Пакетных задач
	утилитных скриптов

Основные поля:

apiVersion: batch/v1
kind: Job
metadata:
  name: pi
spec:
  completions: 5
  parallelism: 2
  backoffLimit: 4
  template:
    spec:
      containers:
      - name: pi
        image: perl
        command: ["perl",  "-Mbignum=bpi", "-wle", "print bpi(2000)"]
      restartPolicy: Never
- **completions** — сколько раз задача должна выполниться успешно.
- **parallelism** — сколько Pod’ов можно запускать одновременно.
- **backoffLimit** — сколько раз перезапускать Pod при ошибке (по умолчанию 6).
- **restartPolicy** — для Job = `Never` или `OnFailure`.

### Как работает

- Job создаёт Pod'ы по шаблону
- Если Pod завершился успешно -> учитывается как выполненный
- Если Pod упал -> может быть перезапущен или создан новый Pod
- Когда выполнено `completions` успешных запусков -> Job считается завершённым

### Отличия от Deployment

- Deployment поддерживает постоянный пул подов
- Job = гарантированное завершение задачи
[[Job]]
[[Сущности]]