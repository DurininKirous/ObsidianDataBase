---
sr-due: 2025-12-01
sr-interval: 86
sr-ease: 270
---

#sr-due 
### Когда `-p 8080:80`:
- `PREROUTING` → `DNAT` на IP контейнера:80
- `POSTROUTING` → `SNAT` (MASQUERADE)
iptables -t nat -L -n -v

[[iptables и NAT]]
[[Docker Network]]