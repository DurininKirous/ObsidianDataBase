---
sr-due: 2026-02-02
sr-interval: 80
sr-ease: 226
---

#sr-due 
Изменяет или валидирует объект до сохранения в etcd.
Разбито на две части:
- Mutating Admission Plugins (например, `DefaultStorageClass`, `DefaultTolerationSeconds`, то есть добавить что-то, изменить)
- Validating Admission Plugins (например, `LimitRanger`, `ResourceQuota`, `SecurityContextDeny`, например, отклонить под с привилегиями)
Идут в следующем порядке:
1. MutatingAdmissionPlugins
2. ObjectSchemaValidation
3. ValidatingAdmissionPlugins

Без него:
- Нельзя применять политики безопасности (PodSecurity, LimitRange)
- Некоторые значения не будут подставляться автоматически (default serviceAccount, default SC)
[[Admission Chain (по пути в etcd)]]
[[Структура внутри apiserver]]