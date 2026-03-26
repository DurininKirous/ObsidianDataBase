---
created: 2026-02-04 08:19
tags:
  - status/seed
  - type/concept
  - domain/linux
  - sr-due
sr-due: 2027-03-11
sr-interval: 400
sr-ease: 290
---
### 💡 The What
*Что это?*
## Входящий пакет

eth0 -> PREROUTING
		↓
	Routing Decision
	↓                     ↓
	INPUT        FORWARD
	   ↓                  ↓
   local proc     POSTROUTING

## Исходящий пакет

local process → OUTPUT
               ↓
          POSTROUTING

### ⚙️ The Why & How
*Инженерная суть. Механика. Зачем это нужно?*
- PREROUTING: для изменения dest ip (dnat) до решения маршрутизации
- INPUT: фильтровать пакеты, адресованные локальному хосту 
- FORWARD: фильтровать пакеты, проходящие через хост
- OUTPUT: контролировать исходящие пакеты от локальных процессов
- POSTROUTING: менять source ip  перед отправкой наружу

---
### 🔗 Connections
- **Родитель**: [[iptables]], [[Последовательность обработки пакетов в netfilter]]
