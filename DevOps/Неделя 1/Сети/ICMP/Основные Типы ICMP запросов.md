---
sr-due: 2026-04-24
sr-interval: 161
sr-ease: 230
---

#sr-due 

| Type | Code | Что значит                                                                                                          |
| ---- | ---- | ------------------------------------------------------------------------------------------------------------------- |
| 8    | 0    | Echo Request - Запрос (Ping)                                                                                        |
| 0    | 0    | Echo Reply  - Ответ на Ping                                                                                         |
| 11   | 0    | Time Exceeded: TTL expired in transit (пришли к роутеру с TTL=0). TTL - счётчик сколько роутеров пакет может пройти |
| 11   | 1    | Fragment reassembly time exceeded (не смогли собрать все фрагменты пакета, пакет «протух»)                          |
| 3    | 0    | Network Unreachable                                                                                                 |
| 3    | 1    | Host Unreachable                                                                                                    |
| 3    | 3    | Port Unreachable (UDP часто)                                                                                        |
| 3    | 4    | Fragmentation needed but DF set (Если MTU мал, а фрагментация запрещена)                                            |
| 5    | 0-3  | Redirect                                                                                                            |
[[Основные Типы ICMP запросов]]
[[ICMP]]