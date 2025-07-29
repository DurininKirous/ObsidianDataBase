---
sr-due: 2025-08-21
sr-interval: 24
sr-ease: 270
---

#sr-due 
### Когда `-p 8080:80`:
- `PREROUTING` → `DNAT` на IP контейнера:80
- `POSTROUTING` → `SNAT` (MASQUERADE)
iptables -t nat -L -n -v

[[iptables и NAT]]
[[Docker Network]]