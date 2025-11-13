---
sr-due: 2025-11-22
sr-interval: 12
sr-ease: 230
---

#sr-due 
"Насколько ресурс ждут?"
Смысл:
	Когда очередь запросов растёт, а ресурс не успевает их обрабатывать.
	Saturation показывает backlog - уровень ожидания
**Примеры:**
- **CPU**: run queue > количество ядер (`loadavg` / `vmstat r`).
- **Disk I/O**: очередь запросов (`await`, `avgqu-sz` в `iostat`).
- **Network**: переполненные буферы, дропы пакетов.
- **Memory**: свопинг, high page fault rate.
- **Threads**: блокировки, mutex contention.
[[Saturation]]
[[USE Method]]