---
sr-due: 2025-12-03
sr-interval: 37
sr-ease: 230
---

#sr-due 
- RED (Rate, Errors, Duration) - три сигнала для пользовательских сервисов:
	- Rate - сколько запросов/секунда
	- Errors - доля неуспешных (5xx, timeouts)
	- Duration - латентность (p95/p99)
- USE (Utilization, Saturation, Errors) - три сигнала для ресурсов:
	- Utilization - % загрузки CPU/диска/сети
	- Saturation - очередь, показатель "насколько близко к пределу"
	- Errors - реальные ошибки (дропы пакетов, ошибки дисков)
В продакшене мы всегда хотим иметь: RED для сервисов, USE для инфраструктуры.
[[RED и USE]]
[[SLO-фрейм + RED USE]]