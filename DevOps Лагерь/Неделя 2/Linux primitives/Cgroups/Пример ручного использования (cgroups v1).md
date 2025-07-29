---
sr-due: 2025-08-04
sr-interval: 14
sr-ease: 270
---

#sr-due 
Создать директорию для cgroup:
`makdir /sys/fs/cgroup/memory/mygroup`
Лимит по памяти:
`echo 100000000 > /sys/fs/cgroup/memory/mygroup/memory.limit_in_bytes`
Добавим процесс в группу:
`echo 12345 > /sys/fs/cgroup/memory/mygroup/tasks`
[[Пример ручного использования (cgroups v1)]]
[[Cgroups]]