---
sr-due: 2026-04-10
sr-interval: 92
sr-ease: 230
---

#sr-due 
- Роль: лёгкий сетевой менеджер для серверов/минимальных систем. Настраивает интерфейсы, VLAN, bond/bridge, статические маршруты, DHCP клиент/сервер
- Юниты/сервисы: systemd-networkd.service; мониторинг: systemd-networkd-wait-online.service
- Конфиг: /etc/systemd/network/.network, .link, .netdev
- Инструменты: networkctl status, networkctl list, journalctl -u systemd-networkd
- Интеграция: зависимости сервисов можно строить от "сеть готова" (`After=network-online.target` + `Wants=systemd-networkd-wait-online.service`)
[[networkd - networking]]
[[systemd - PID 1 (main daemon)]]