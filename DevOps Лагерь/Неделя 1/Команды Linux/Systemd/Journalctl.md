---
sr-due: 2025-09-15
sr-interval: 40
sr-ease: 250
---

#sr-due 
*journalctl -f* - аналог tail -f, то есть в реальном времени логи выводит
*journalctl -u unit* - логи по определённому юниту выводить
*journalctl -b* - логи с последнего запуска системы
*journalctl -b -n - логи с предыдущего n-ого запуска
*journalctl --since* - логи с определённого времени, пример - "2 hours ago"
*journalctl --disk-usage* - размер journal показать
*journalctl --vacuum-time=7d* - очистить логи старше 7 дней
journalctl -p 3/6/9 - логи с различными метками важности/типом информации
[[Journalctl]]
[[Systemd]]