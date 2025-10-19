---
sr-due: 2025-10-23
sr-interval: 4
sr-ease: 210
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