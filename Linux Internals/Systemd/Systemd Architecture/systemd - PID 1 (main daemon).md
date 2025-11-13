---
sr-due: 2025-11-23
sr-interval: 14
sr-ease: 234
---

#sr-due 
- Роль: первый пользовательский процесс; оркестратор всех unit'ов (service, socket, timer, path, target, mount ...); управление зависимостями, параллельный старт/стоп, слежение через cgroups
- Юниты/демоны: сам systemd (PID 1) + менеджеры системного/пользовательского уровня
- Конфигурация: unit-файлы в /usr/lib/systemd/system/ и overrides в /etc/systemd/system
- **Ключевые действия:** `systemctl start|stop|restart <unit>`, `enable|disable`, `status`, `daemon-reload`, `list-dependencies`
- Диагностика загрузки: systemd-analyze time|blame|critical-chain
- Гарантии: знает реальную готовность сервиса (через `Type=notify`/socket-активацию), убивает/перезапускает всю cgroup сервиса, а не одиночный PID
[[systemd - PID 1 (main daemon)]]
[[Systemd]]