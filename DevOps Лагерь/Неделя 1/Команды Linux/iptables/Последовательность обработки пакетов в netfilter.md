---
sr-due: 2025-09-11
sr-interval: 45
sr-ease: 290
---

#sr-due 
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


## Зачем нужны цепочки 

PREROUTING: для изменения dest ip (dnat) до решения маршрутизации
INPUT: фильтровать пакеты, адресованные локальному хосту 
FORWARD: фильтровать пакеты, проходящие через хост
OUTPUT: контролировать исходящие пакеты от локальных процессов
POSTROUTING: менять source ip  перед отправкой наружу
[[Последовательность обработки пакетов в netfilter]]
[[iptables]]