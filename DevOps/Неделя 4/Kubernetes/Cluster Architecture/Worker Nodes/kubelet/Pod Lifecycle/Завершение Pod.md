---
sr-due: 2026-03-18
sr-interval: 39
sr-ease: 210
---

#sr-due 
1. В API ставится `deletionTimestamp` + gracePeriod
2. kubelet шлёт SIGTERM процессу 1 в контейнере(ах)
3. Если задан `preStop`, он выполняется перед SIGTERM
4. readiness падает сразу (Pod исключают из endpoints), трафик прекращается
5. По истечении `terminationGracePeriodSeconds` - SIGKILL
6. kubelet запускает CNI DEL, размонтирует тома; Pod удаляется из API.
Примечание:
- При evict или при RollingUpdate поведение завершения такое же
- Если процесс "подвис" и игнорирует SIGTERM, прибьётся SIGKILL по таймауту
[[Завершение Pod]]
[[Pod Lifecycle]]