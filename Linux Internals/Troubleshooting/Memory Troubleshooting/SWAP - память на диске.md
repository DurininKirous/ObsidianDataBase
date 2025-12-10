---
sr-due: 2025-12-20
sr-interval: 27
sr-ease: 230
---

#sr-due 
Swap - это резервная память, но медленная. Когда RAM заполнена, страницы выгружаются на диск.

Проверка активности swap:
```bash
vmstat 1
```
- si (swap in), so (swap out) - >0 постоянно -> нехватка RAM
Проверка размера и использования:
```bash
swapon --show
free -h
```

Настройка поведения:
```bash
cat /proc/sys/vm/swappiness
sysctl -w vm.swappines=10
```
- Значение 0-100: чем выше, тем активнее Linux использует swap
- На серверах обычно ставят 10-20, чтобы swap был аварийным, а не обычным
[[SWAP - память на диске]]
[[Memory Troubleshooting]]