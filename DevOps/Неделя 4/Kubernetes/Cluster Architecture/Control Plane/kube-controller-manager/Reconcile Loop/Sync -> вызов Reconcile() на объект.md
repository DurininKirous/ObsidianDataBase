---
sr-due: 2026-08-06
sr-interval: 173
sr-ease: 210
---

#sr-due 
Контроллер вызывает Reconcile(key string):
1. Получает объект из кеша informer'а
2. Смотрит .spec и .status
3. Анализирует текущее состояние мира (например, сколько подов запущено реально) 
[[Sync -> вызов Reconcile() на объект]]
[[Reconcile Loop (контроллерный цикл)]]