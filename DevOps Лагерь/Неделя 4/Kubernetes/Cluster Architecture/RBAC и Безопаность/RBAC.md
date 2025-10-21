---
sr-due: 2025-11-03
sr-interval: 13
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