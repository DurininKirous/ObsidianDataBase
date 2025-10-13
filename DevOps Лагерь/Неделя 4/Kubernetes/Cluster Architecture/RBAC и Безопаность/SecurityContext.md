---
sr-due: 2025-10-14
sr-interval: 1
sr-ease: 230
---

#sr-due 
Позволяет задавать ограничения безопаности для контейнера:
```yaml
securityContext:
	RunAsUser: 1001
	runAsGroup: 1001
	fsGroup: 2000
	readOnlyRootFilesystem: true
	allowPrivilegeEscalation: false
	capabilities:
		drop: ["ALL"] 
```

Назначение:
- Запуск пода не от root
- Ограничение доступа к файловой системе
- Отключение системных capabilities
[[SecurityContext]]
[[RBAC и безопаность в Kubernetes]]