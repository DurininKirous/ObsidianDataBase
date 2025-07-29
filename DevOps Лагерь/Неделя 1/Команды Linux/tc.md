---
sr-due: 2025-09-10
sr-interval: 44
sr-ease: 290
---

#sr-due 
Утилита для создания различных нагрузочныхи и тестовых условий в средне. позволяет  задержки, потери пакетов создавать и так далее.
Задержка: sudo tc qdisc add dev eth0 root netem delay 200ms
Потери: sudo tc qdisc change dev eth0 root netem loss 10%
Убрать: sudo tc qdisc del dev eth0 root
[[tc]]
[[Команды Linux]]