---
sr-due: 2026-02-04
sr-interval: 111
sr-ease: 230
---

#sr-due 

| Namespace | Изолирует                                          | Команда `unshare`/`-t` |
| --------- | -------------------------------------------------- | ---------------------- |
| mnt       | Точки монтирования                                 | -m                     |
| pid       | Процессы (их PID дерево)                           | -p                     |
| net       | Сетевые интерфейсы, iptables rules, routing tables | -n                     |
| uts       | Hostname, domainname                               | -u                     |
| ipc       | System V IPC, POSIX message queues                 | -i                     |
| user      | uid, gid видимость (mapping uid 0 -> non-root)     | -U                     |
| cgroup    | Группы cgroups (cgroup namespaces)                 | -C                     |
[[Типы namespaces]]
[[Namespaces]]