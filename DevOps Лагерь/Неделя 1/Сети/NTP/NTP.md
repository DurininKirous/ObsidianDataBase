---
sr-due: 2025-08-21
sr-interval: 24
sr-ease: 250
---

#sr-due 
# 🕰️ NTP (Network Time Protocol)

## 📌 Зачем нужен
- Синхронизировать часы между серверами/клиентами.
- Для правильных логов, SSL/TLS, Kerberos, Kafka offset.
- Поддерживает точность до миллисекунд.

## 🚀 Архитектура (stratum)
| Stratum | Кто это                               |
|---------|--------------------------------------|
| 0       | Reference clocks (GPS, атомные)      |
| 1       | Серверы, напрямую подключенные к stratum 0 |
| 2       | Серверы, синхронизирующиеся со stratum 1 |
| 3+      | Клиенты/серверы дальше по цепочке    |

Client  
|  
Resolver / NTP client  
|  
NTP server (stratum 2)  
|  
NTP server (stratum 1)  
|  
GPS / атомные часы (stratum 0)


## 📦 Структура NTP packet (UDP/123)
- **LI (2 bits)** — leap indicator (нет синхрона)
- **VN (3 bits)** — версия протокола
- **Mode (3 bits)** — 3=client, 4=server
- **Stratum** — уровень сервера
- **Poll** — интервал опроса
- **Precision** — точность
- **Root Delay, Root Dispersion** — задержки до источника
- **Reference Timestamp** — когда был синхронизирован
- **Originate Timestamp** — когда клиент отправил запрос
- **Receive Timestamp** — когда сервер получил
- **Transmit Timestamp** — когда сервер отправил

Эти временные метки позволяют клиенту оценить offset и задержку RTT.

## 🛠 Основные утилиты
### chrony (часто на новых Linux)
bash
chronyc tracking
chronyc sources -v

[[NTP]]
[[Сети]]