---
sr-due: 2025-10-11
sr-interval: 15
sr-ease: 210
---

#sr-due 
- Используется informer - подписка на изменения конкретного ресурса (например, Deployment)
- informer слушает kube-apiserver через LIST + WATCH
- Все изменения (create / update / delete) -> события (events)
Watch не делает контроллер сам. Он работает через **SharedInformerFactory** .
[[Watch (подписка на изменения)]]
[[Reconcile Loop (контроллерный цикл)]]