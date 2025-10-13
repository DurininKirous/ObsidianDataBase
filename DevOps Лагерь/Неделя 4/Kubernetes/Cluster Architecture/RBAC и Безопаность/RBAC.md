---
sr-due: 2025-10-14
sr-interval: 1
sr-ease: 230
---

#sr-due 
RBAC управляет доступом по схеме:
	Subject (SA/User/Group) -> Role/ClusterRole (rules) -> Binding (RoleBinding/ClusterRoleBinding)
- Role - права внутри одного namespace
- ClusterRole - глобальные права
- RoleBinding - привязка Role к субъекту (SA/User/Group)
- ClusterRoleBinding - глобальная привязка

Пример цепочки:
- ServiceAccount `reader`
- Role `read-pods` (разрешает `get`, `list`, `watch` на `pods`)
- RoleBinding `read-pods-binding` -> связывает SA с Role
[[RBAC]]
[[RBAC и безопаность в Kubernetes]]