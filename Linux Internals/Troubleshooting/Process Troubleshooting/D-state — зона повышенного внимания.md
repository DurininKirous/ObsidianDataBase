---
sr-due: 2026-03-31
sr-interval: 82
sr-ease: 230
---

#sr-due 
**Что значит:** поток в ядре, чаще всего ждёт I/O (диск, сеть, NFS, FUSE, блокировки драйвера).  
**Признаки:**
- `STAT` = `D`, процесс “неубиваем” `kill -9` (сигналы доставятся только после выхода из ядра).
- `wchan` в `ps`/`/proc/<pid>/wchan` показывает точку ожидания (например, `io_schedule`, `nfs_wait_*`, `wait_on_page_bit`).

**Действия:**
```bash
ps -eo pid,ppid,stat,wchan:24,cmd | grep ' D '
# ps — находишь D-state и точку ожидания

sudo iostat -xz 1
# iostat — смотри latency/queue/util дисков (подтверждение I/O-проблемы)

sudo smartctl -H /dev/sdX
# smartctl — здоровье диска, исключить “железо”

dmesg -T | egrep -i 'blk|i/o error|reset|scsi|nvme|ext4|xfs|nfs'
# dmesg — ошибки устройств/ФС/драйверов
```
Если `wchan` указывает на NFS/FUSE/сетевой стек — проверь доступность сервера, latency сети, логи демонов.
[[D-state — зона повышенного внимания]]
[[Process Troubleshooting]]