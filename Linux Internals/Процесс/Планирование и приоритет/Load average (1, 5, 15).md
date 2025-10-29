---
sr-due: 2025-10-31
sr-interval: 2
sr-ease: 230
---

#sr-due 
`/proc/loadavg` и `uptime` показывают среднюю **нагрузку** за 1/5/15 минут. В Linux **load average** ≠ «CPU utilization».

**Что входит в load:** число задач в состояниях **R (running/runnable)** **+ D (uninterruptible I/O sleep)**. Поэтому медленный диск может поднимать load даже при низком %CPU.

Как интерпретировать:
- На N‑ядерной системе «правило большого пальца»: load≈N → CPU насыщен; сильно >N → очереди растут.
- Высокий load при низком CPU → ищи I/O‑узкие места, блокировки, NFS/диски.

Проверка и диагностика:
```bash
cat /proc/loadavg
vmstat 1 # r (run queue), b (blocked/uninterruptible)
iostat -xz 1 # узкие места диска
pidstat -d 1 # I/O по процессам
```
Современное дополнение: **PSI (Pressure Stall Information)** — `/proc/pressure/{cpu,io,memory}` показывает «сколько времени система была под давлением». Полезно для алертов.
[[Load average (1, 5, 15)]]
[[Планирование и приоритет]]