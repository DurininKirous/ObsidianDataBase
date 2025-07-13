---
sr-due: 2025-07-14
sr-interval: 1
sr-ease: 230
---

#sr-due 
Низкоуровневая утилита для изучения пакетов, гуляющих в трафике
Примеры работы:
tcpdump -i (interface) (port)
tcpdump -i any - любые интерфейсы слушать
tcpdump port 80 - слушать пакеты на порте 80
tcpdump src (ip) - просмотреть пакеты от указанного ip
tcpdump dst (ip) - просмотреть пакеты к указанному ip
tcpdump 'tcp[tcpflags] & tcp-syn/другой флаг != 0'

tcpdump 'tcp[tcpflags] & tcp-syn != 0' - SYN пакеты (начало соединений)
tcpdump 'tcp[tcpflags] & tcp-ack != 0' - ACK пакеты
tcpdump 'tcp[tcpflags] & tcp-fin != 0' - FIN (закрытие)
tcpdump 'tcp[tcpflags] & tcp-rst != 0' - RST (сбросы)
tcpdump 'tcp[tcpflags] & tcp-psh != 0' - PSH (толкнуть сразу)

tcpdump -A -s 0 port 80 - в ASCII и HEX посмотреть внутренности пакетов
tcpdump port 53 - посмотреть пакет на dns порту
tcpdump -vvv "protocol" - посмотреть трафик конкретного протокола
[[Tcpdump]]
[[Команды Linux]]