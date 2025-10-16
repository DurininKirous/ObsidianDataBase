---
sr-due: 2025-10-21
sr-interval: 5
sr-ease: 230
---

#sr-due 
- Каждый Pod в Kubernetes всегда запускается от имени ServiceAccount. По умолчанию - default в своём namespace
- SA - это "технический пользователь" для подов и контроллеров, у которого есть токен (/var/run/secrets/kubernetes.io/serviceacount/token)
- Этот токен используется при обращении к API-серверу

Ключевые моменты:
- Можно создать свой SA и привязать его к Pod через:
```yaml
spec:
	serviceAccountName: my-sa
```
- Можно ограничить или расширить права через Role/ClusterRole

[[ServiceAccount]]
[[RBAC и безопаность в Kubernetes]]
