---
sr-due: 2025-11-17
sr-interval: 73
sr-ease: 250
---

#sr-due 
### Принимает путь для config.json
`runc run "container-id"`
В каталоге ./container-id должен быть:
- config.json - описание контейнера (по oci spec)
- rootfs/ - root файловая система контейнера
### Парсит конфиг
- Какие namespaces включить (CLONE_NEWNS, CLONE_NEWPID, ...)
- Какой cmd запустить
- Какие лимиты (memory, cpu) через cgroups
- Какой rootFS (обычно overlayFS)
### Создаёт процесс
- clone() с нужными флагами namespace
- setns() при необходимости
- mount() overlayFS
- pivot_root() чтобы root стал rootfs/
- write() в /sys/fs/cgroup/... для ограничения
- и, наконец, execve() запускает команду (например, nginx)

[[Что runc делает]]
[[runc]]