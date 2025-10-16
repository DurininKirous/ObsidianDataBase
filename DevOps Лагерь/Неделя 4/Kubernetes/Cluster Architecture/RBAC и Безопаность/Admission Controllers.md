---
sr-due: 2025-10-21
sr-interval: 5
sr-ease: 230
---

#sr-due 
Компоненты API Server, которые проверяют или модифицируют манифесты
- ValidatingAdmissionWebhook - проверяет, можно ли принять объект
- MutatingAdmissionWbhook - может изменять объект (например, доббавлять аннотации)
- Примеры встроенных контроллеров:
	- `NamespaceLifecycle`
	- `LimitRanger`
	- `PodSecurity`
[[Admission Controllers]]
[[RBAC и безопаность в Kubernetes]]