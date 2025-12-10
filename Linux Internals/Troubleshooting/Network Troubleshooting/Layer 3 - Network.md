---
sr-due: 2025-12-21
sr-interval: 28
sr-ease: 230
---

#sr-due 
**Вопросы:** есть IP? маршрут? ходит ли до шлюза/наружу? не блокирует ли firewall?
```bash
ip addr show              # ip — адреса/маски на интерфейсе
ip route show             # ip — таблица маршрутов (default via ...)
ping -c2 <gateway>        # ping — связность с шлюзом
ping -c2 1.1.1.1          # ping — внешняя IP-связность
iptables -L -n -v         # iptables — правила фильтра, счётчики попаданий
nft list ruleset          # nft — правила nftables (если используется)
```
- Нет `default via` → нет выхода в интернет.
- До шлюза пингуется, наружу — нет → upstream/firewall/NAT.
- Высокий RTT/потери → перегрузка/ошибки L1/L2/L3 по пути.

**Действия:** добавить/починить маршрут, проверить политики (iptables/nft), ACL на границе, NAT/маскарадинг.
[[Layer 3 - Network]]
[[Network Troubleshooting]]