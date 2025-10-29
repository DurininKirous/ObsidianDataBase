#sr-due 
- Роль: сбор и хранение логов с метаданными (unit, UID, cgroup, PID, PRIORITY, _EXE_, _CMDLINE_). Пишет в память и/или нна диск (journal files)
- Юнит: systemd-journald.service
- Конфиг: /etc/systemd/journald.conf (Например, Storage=auto|persistent, лимиты)
- Чтение: journalctl (фильтры: -u unit, -b, -f, -p warning, _PID_=, _SYSTEMD_UNIT=_)
- Интеграция: любые сервисы под systemd автоматически снабжаются метаданными; логгеры типа rsyslog могут читать из журнала; forwarding на удалённые хранилища поддерживвается через шлюзы
[[journald - logging]]
[[systemd - PID 1 (main daemon)]]