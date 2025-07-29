---
sr-due: 2025-08-11
sr-interval: 14
sr-ease: 210
---

#sr-due 
1. Образ загружается и сохраняется в content store
2. Создаётся snapshot (обычно overlayFS) на основе rootFS образа (это rw snapshot, по сути diff папка в docker)
3. Через runc создаётся контейнер:
	- Mount namespace, PID namespace и проч.
	- pivot_root, execve
4. shim остаётся жить рядом с контейнером: он управляет его stdout, stderr, exit-кодом, сигналами и т.п.
5. containerd может быть перезапущен - контейнеры продолжают работать

### Файловая структура
- /run/containerd/ - runtime-информация, сокеты, shim'ы
- /var/lib/containerd/ - snapshots, images, content stort
- /etc/containerd/config.toml - конфигурация демона
[[Жизненный цикл контейнера в containerd]]
[[containerd]]