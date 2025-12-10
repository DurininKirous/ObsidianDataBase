---
sr-due: 2025-12-22
sr-interval: 29
sr-ease: 230
---

#sr-due 
**Вопросы:** корректный MAC? ARP работает? нет ли проблем на свитче/VLAN?
```bash
ip link show dev eth0     # ip — MAC-адрес интерфейса
ip neigh                   # ip neigh — ARP-таблица (IP↔MAC, состояние REACHABLE/STALE/FAILED)
```
- Записи `FAILED/INCOMPLETE` → ARP не резолвится (VLAN, L2 ACL, свитч).
- Дубли MAC/флап VLAN → периодический обрыв связности.

**Действия:** проверить правильный VLAN/tagging, порт на свитче (access/trunk), spanning-tree/port-security логи.
[[Layer 2 - Data Link]]
[[Network Troubleshooting]]