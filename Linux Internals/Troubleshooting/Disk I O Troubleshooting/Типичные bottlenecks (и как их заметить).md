---
sr-due: 2025-11-21
sr-interval: 11
sr-ease: 230
---

#sr-due 
- High latency: awai/r_await/w_await растут -> пользователи/БД жалуются на подвисания
- High queue depth: avgqu-sz grows -> запросы скапливаются
- 100% utilization: %util~100% устойчиво -> диск всегда под загрузкой
- Writers storm: много процессов пишу (логи/бэкапы) -> конкуренция на журнал ФС/устройство
[[Типичные bottlenecks (и как их заметить)]]
[[Disk I O Troubleshooting]]