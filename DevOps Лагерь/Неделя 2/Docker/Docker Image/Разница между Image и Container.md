---
sr-due: 2025-08-19
sr-interval: 22
sr-ease: 246
---

#sr-due 

| Характеристика    | Image (образы)                | Container (контейнеры)                |
| ----------------- | ----------------------------- | ------------------------------------- |
| Состояние         | Read-only                     | Read-write snapshot                   |
| Использование     | Шаблон для запуска            | Исполняемое окружение                 |
| Расположение      | /var/lib/docker/overlay2      | /var/lib/docker/overlay2 + snapshot   |
| Что содержит      | Слои (.tar), config, manifest | Всё из image + upperdir + процесс PID |
| Идентификатор     | sha256 hash                   | UUID (или имя контейнера)             |
| Управляется через | `docker image`                | `docker container` или `docker ps`    |
[[Разница между Image и Container]]
[[Docker Image]]