---
sr-due: 2025-11-08
sr-interval: 30
sr-ease: 230
---

#sr-due 
Поскольку статический под запущен **в обход API**, его «не видно» kubectl/сервисам.  
kubelet создаёт в API **зеркальный объект** — _mirror pod_:
- Отражает метаданные/статус static pod’a, чтобы:
    - `kubectl get/describe/logs/exec` работали,
    - сервисы могли выбирать под по **labels**,
    - контроллеры видели его `status`.
- Создаётся kubelet’ом автоматически, когда API доступен.
Характерные детали mirror pod:
- Имя: `<name>-<nodeName>` (чтобы не было конфликтов между нодами).
- Аннотации наподобие: `kubernetes.io/config.mirror`, `kubernetes.io/config.source: file|http` (служебные для API/kubelet).
- **Не планируется** и **не управляется** scheduler’ом/Deployment’ом — это просто «витрина».
[[Mirror Pod]]
[[kubelet]]