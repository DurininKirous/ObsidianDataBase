---
sr-due: 2026-12-27
sr-interval: 279
sr-ease: 210
---

#sr-due 
Пример:
`docker run -it alpine sh`
Пошагово:
1. docker CLI отправляет HTTP POST на dockerd через /var/run/docker.sock
2. dockerd:
	- парсит команду
	- проверяет наличие образа (pull если нужно)
	- генерирует полный OCI config.json
3. Вызывает containerd:
	- создаёт snapshot (read-only слои + rw upperdir)
	- генерирует директорию с rootfs
	- запускает shim -> вызывает runc
4. Контейнер стартует
5. shim управляет stdin/stdout/signal, возвращает exit-код
6. Все логи и статусы возвращаются через dockerd
[[Что происходит при docker run?]]
[[dockerd]]