---
sr-due: 2025-12-24
sr-interval: 31
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