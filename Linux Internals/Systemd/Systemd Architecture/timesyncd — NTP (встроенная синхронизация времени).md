---
sr-due: 2025-12-26
sr-interval: 33
sr-ease: 230
---

#sr-due 
- Роль: клиент точного времени (SNTP/NTP) из коробки для большинства хостов
- Юнит: systemd-timesyncd.service
- Конфиг: /etc/systemd/timesyncd.conf
- Статус: timedatectl status (покажет источник времени), journaldctl -u systemd-timesyncd
- Интеграция: стартует рано, чтобы временные метки и TLS были корректны; кооперируется с timedatectl (включение NTP)
[[timesyncd — NTP (встроенная синхронизация времени)]]
[[systemd - PID 1 (main daemon)]]