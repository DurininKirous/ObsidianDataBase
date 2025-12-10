---
sr-due: 2026-01-23
sr-interval: 70
sr-ease: 206
---

#sr-due 
Проверяет:
- имеет ли пользователь право на действие (например: create pods в default)
- поддерживает:
	- RBAC
	- ABAC
	- Node authorizer
	- Webhook authorizer
Как реализует:
- Читает из RBAC/ABAC/NodePolicy
- Оценивает: можно ли делать verb resource в namespace
- Использует SubjectAccessReview
Без него:
- Любой аутентифицированный пользователь сможет делать что угодно
- RBAC полностью перестанет работать
[[Authorizer (разрешает действие)]]
[[Структура внутри apiserver]]