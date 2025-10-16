---
sr-due: 2025-10-17
sr-interval: 1
sr-ease: 210
---

#sr-due 
Новые уровни безопаности вместо PSP (PodSecurityPolicy)
Уровни:
- `priveleged` - всё разрешено (для системных ns)
- `baseline` - базовая защита (минимум привелегий)
- `restricted` - строго: без root, без hostPath, без привелегий
Пример аннотаций для namespace:
```bash
kubectl label ns dev \
	pod-secutiry.kubernetes.io/enforce=restricted \
	pod-secutiry.kubernetes.io/audit=restricted \
	pod-securiry.kubernetes.io/warn=restricted
```
[[PodSecurityStandards]]
[[RBAC и безопаность в Kubernetes]]