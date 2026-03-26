---
created: 2026-01-28 19:05
tags:
  - status/seed
  - type/concept
  - domain/k8s
  - sr-due
sr-due: 2026-07-03
sr-interval: 156
sr-ease: 210
---
### 💡 The What
*Что это?*
Watch механизм позволяет подписываться на изменения какого-то ресурса и сразу получать уведомление, когда отслеживаемый объект был изменён

### ⚙️ The Why & How
*Инженерная суть. Механика. Зачем это нужно?*
- Используется informer ([[SharedInformerFactory и Informer]]) - подписка на изменения конкретного ресурса (например, Deployment)
- informer слушает [[kube-apiserver]] через LIST + WATCH ([[Reflector в Informer в K8S]])
- Все изменения (create / update / delete) -> события (events)
Watch не делает контроллер сам. Он работает через **SharedInformerFactory** .

---
### 🔗 Connections
- **Родитель**: [[SharedInformerFactory и Informer]]
- **Влияет на**: [[PLEG (Pod Lifecycle Event Generator) в k8s]]
