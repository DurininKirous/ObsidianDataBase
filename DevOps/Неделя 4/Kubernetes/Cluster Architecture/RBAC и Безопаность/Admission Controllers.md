---
sr-due: 2026-07-24
sr-interval: 160
sr-ease: 230
---

#sr-due 
Компоненты API Server, которые проверяют или модифицируют манифесты
- ValidatingAdmissionWebhook - проверяет, можно ли принять объект
- MutatingAdmissionWebhook - может изменять объект (например, доббавлять аннотации)
- Примеры встроенных контроллеров:
	- `NamespaceLifecycle`
	- `LimitRanger`
	- `PodSecurity`
[[Admission Controllers]]
[[RBAC и безопаность в Kubernetes]]