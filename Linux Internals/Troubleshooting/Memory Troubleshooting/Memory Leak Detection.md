---
sr-due: 2025-11-23
sr-interval: 13
sr-ease: 230
---

#sr-due 
Как заподозрить утечку:
- RSS процесса постоянно растёт при стабильной нагрузке
- "available" падает, хотя активных задач не прибавилось
Диагностика:
1. Снимай pidstat -r -p pid 5 - следи за ростом vsz/rss
2. Для C/C++ - valgrind: инструмент анализа утечек памяти:
```bash
valgrind --leak-check=full ./program
```
➜ Отслеживает непросвобождённые участки памяти (malloc/free).
3. Для других языков:
	- **Go:** `pprof` (`go tool pprof -http=:8080 mem.prof`)
	- **Python:** `tracemalloc`, `objgraph`
	- **Java:** `jmap -dump:live,format=b,file=heap.bin` + анализ в VisualVM. 
[[Memory Leak Detection]]
[[Memory Troubleshooting]]