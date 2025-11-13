---
sr-due: 2025-11-12
sr-interval: 9
sr-ease: 250
---

#sr-due 
Назначение: заранее открывает сокет(ы) и будит связанный .service при первом соединении
Связь: имя совпадает: foo.socket <-> foo.service (или Service= явным полем).
Ключевые поля (\[Socket]):
- ListenStream=, ListenDatagram=, ListenSequentialPacket=, ListenFIFO=, ListenNetlink=, ListenUSBFunction=.
- Accept= (yes для инстанс-сервисов типа inetd; тогда будет foo@\<connid>.service)
- SocketMode=, SocketUser=, SocketGroup=, Backlog=
Типичный цикл:
1. systemctl enable --npw foo.socket
2. Первый connect -> systemd запускает foo.service, передаёт уже открытый FD
Проверка:
```bash
systemctl status foo.socket
ss -ltnp | grep <port>
journalctl -u foo.socket -b
```
[[socket]]
[[Units]]