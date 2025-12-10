---
sr-due: 2026-01-28
sr-interval: 54
sr-ease: 250
---

#sr-due 
**Вопросы:** есть ли линк? корректны ли скорость/дуплекс? ошибки на интерфейсе?
```bash
ip link show dev eth0     # ip link — состояние интерфейса/линка (UP/DOWN, ошибки)
ethtool eth0              # ethtool — скорость/дуплекс/автосогласование/линк
ethtool -S eth0           # ethtool -S — счётчики ошибок/дропов/CRC на NIC
```
- `state DOWN` или `NO-CARRIER` → кабель/порт/вилка/свитч.
- Ошибки (`rx_crc_errors`, `rx_dropped`) растут → кабель/порт/дуплекс-миcматч.
- Speed/Duplex mismatch → флап, ретраи, низкая пропускная.

**Действия:** заменить кабель, зафиксировать скорость/дуплекс симметрично, проверить другой порт свитча.
[[Layer 1 - Physical]]
[[Network Troubleshooting]]