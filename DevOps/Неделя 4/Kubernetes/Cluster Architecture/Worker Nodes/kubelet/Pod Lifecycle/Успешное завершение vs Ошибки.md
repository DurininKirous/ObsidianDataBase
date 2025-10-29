---
sr-due: 2025-11-27
sr-interval: 37
sr-ease: 210
---

#sr-due 
- Если **все контейнеры** завершились с кодом 0 и `restartPolicy=Never/OnFailure` ⇒ phase=`Succeeded`.
- Если контейнер завершился с ошибкой и исчерпан бэкофф/лимиты ⇒ phase=`Failed`.
- Для `restartPolicy=Always` Pod часто остаётся `Running`, даже если контейнер перезапускается — смотри `containerStatuses` (restartCount, lastState).
[[Успешное завершение vs Ошибки]]
[[Pod Lifecycle]]