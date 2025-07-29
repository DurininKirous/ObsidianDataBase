---
sr-due: 2025-09-09
sr-interval: 43
sr-ease: 270
---

 #sr-due 
 Утилита для фильтрации трафика в системе Linux через подсистему ядра netfilter.  Позволяет настраивать фильтр пакетов, NAT, изменять TTL и TOS и т.д.
 Это интерфейс для управления сетевыми пакетами, проходящими через:
- Локальный хост (INPUT/OUTPUT)
- Транзит через хост (FORWARD)
- До/После маршрутизации (PREROUTING, POSTROUTING - в таблице nat/mangle)
Управляет:
- фильтрацией (firewall) - DROP/ACCEPT
- NAT/SNAT/DNAT
- Маркировками пакетов, изменением TOS/TTL
- Stateful инспекцией соединений через conntrack

[[iptables]]
[[Команды Linux]]