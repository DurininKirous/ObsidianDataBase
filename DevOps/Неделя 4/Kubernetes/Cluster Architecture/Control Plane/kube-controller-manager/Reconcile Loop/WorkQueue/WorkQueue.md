---
sr-due: 2026-01-31
sr-interval: 63
sr-ease: 210
---

#sr-due 
Это **rate-limited, idempotent, retry-aware очередь ключей**, которая управляет вызовами `Reconcile`
**Ключи** — обычно строки вида `"namespace/name"`,  
которые представляют Kubernetes-объекты (`Pod`, `Deployment`, и т.д.)

> ❗️ Важно: **в WorkQueue не кладутся сами объекты, а только ключи!**  
> Сами данные читаются из кеша через `Lister`.

[[WorkQueue]]
[[Reconcile Loop (контроллерный цикл)]]