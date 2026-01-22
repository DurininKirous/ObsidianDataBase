---
created: 2026-01-06 15:44
tags:
  - status/seed
  - type/concept
  - domain/linux
  - sr-due
sr-due: 2026-04-13
sr-interval: 97
sr-ease: 250
---
### 💡 The What
*Что это?*
В Systemd Unit может иметь тип сервиса socket, позволяет заранее открывать сокет и будит связанный .service при первом соединении.

### ⚙️ The Why & How
*Инженерная суть. Механика. Зачем это нужно?*
Позволяет не держать основной сервис постоянно включённым. Socket берёт на себя роль получения соединений и в  передаёт обработку основному сервису.
Связь: имя совпадает: foo.socket <-> foo.[[ObsidianDataBase/Linux Internals/Systemd/Units/service|service]] (или Service= явным полем).
Ключевые поля (\[Socket]):
- ListenStream=, ListenDatagram=, ListenSequentialPacket=, ListenFIFO=, ListenNetlink=, ListenUSBFunction=.
- Accept= (yes для инстанс-сервисов типа inetd; тогда будет foo@\<connid>.service)
- SocketMode=, SocketUser=, SocketGroup=, Backlog=
Типичный цикл:
1. systemctl enable --npw foo.socket
2. Первый connect -> systemd запускает foo.service, передаёт уже открытый [[File descriptor]]
Проверка:
```bash
systemctl status foo.socket
ss -ltnp | grep <port>
journalctl -u foo.socket -b
```
Пример:
```bash
[Socket]
ListenStream=9999
Accept=no
[Install]
WantedBy=sockets.target
```

---
### 🔗 Connections
- **Родитель**: [[Systemd]], [[Философия Systemd - всё через units]], [[Service types]]
