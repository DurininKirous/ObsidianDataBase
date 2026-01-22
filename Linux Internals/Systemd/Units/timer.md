---
sr-due: 2026-04-08
sr-interval: 90
sr-ease: 230
---

#sr-due 
Назначение: планировщик, который триггерит .service по времени/интервалам. Надёжная замена cron для unit-ов.
Связь: backup.timer <-> backup.service (Или Unit=)
Ключевые поля (\[Timer]):
- OnCalendar= (календарные выражения: daily, Mon..Fri 03:00, \*-\*-01 00:00:00)
- OnUnitActiveSec=, OnUnitInactiveSec= (интервалы от последнего запуска/завершенич)
- AccuracySec= (допуск), RandomizedDelaySec=
- Persistent= (yes - выполнить пропущенные при простое после возобновления)
Команды:
```bash
systemctl enable --now backup.timer
systemctl list-timers
systemctl status backup.timer
journalctl -u backup.service -b
```
[[timer]]
[[Units]]