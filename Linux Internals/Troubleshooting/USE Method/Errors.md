---
sr-due: 2025-11-12
sr-interval: 7
sr-ease: 250
---

#sr-due 
> “Что ломается при работе ресурса?”

**Смысл:**  
Ошибки в использовании ресурса: аппаратные, драйверные, сетевые, программные.  
Не всегда влияют на производительность напрямую, но могут сигнализировать о деградации.

**Примеры:**
- **CPU**: machine check errors, thermal throttling.
- **Memory**: OOM kills, ECC memory errors.
- **Disk**: I/O errors, retries, reallocation.
- **Network**: packet loss, retransmissions.
- **Processes**: segmentation fault, OOM-killer, zombie processes.
[[Errors]]
[[USE Method]]