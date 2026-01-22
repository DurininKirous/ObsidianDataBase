---
sr-due: 2026-12-24
sr-interval: 350
sr-ease: 290
---

#sr-due 
Позволяет поменять параметры ядра, изменяя виртуальную файловую систему /proc/sys/.
Можно менять параметры как через sysctl -w name=value, так и через echo "value" > /proc/sys/...

| Категория  | Примеры                                |
| ---------- | -------------------------------------- |
| fs.*       | file handles, inotify, AIO             |
| net.ipv4.* | TCP, UDP, routing, ip_forwarding       |
| vm.*       | virtual memory: swappiness, overcommit |
| kernel.*   | sysrq, panic_on_oom                    |
![[Pasted image 20250708201438.png]]
В /etc/sysctl.conf можно установить настройки навсегда, одноразовое использование в сессии одной пропадает при перезапуске.

sysctl -p - загрузить настройки из /etc/sysctl.conf

[[Sysctl]]
[[Команды Linux]]