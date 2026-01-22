---
sr-due: 2026-04-06
sr-interval: 88
sr-ease: 230
---

#sr-due 
- Роль: системный резолвер имён с кэшем, DNS-over-TLS/LLMNR/mDNS, split-DNS на интерфейсы/домены
- Юнит: systemd-resolved.service
- Конфиг: /etc/systemd/resolved.conf (+ пер-интерфейсные настройки через networkd)
- Инструменты: resolvectl status|query example.com (или systemd-resolve в сстарых версиях)
- Интеграция: устанавливает системный stub-резолвер на 127.0.0.53 (или по политике дистро); networkd может прописывать DNS прямо в resolved
[[resolved - DNS]]
[[systemd - PID 1 (main daemon)]]