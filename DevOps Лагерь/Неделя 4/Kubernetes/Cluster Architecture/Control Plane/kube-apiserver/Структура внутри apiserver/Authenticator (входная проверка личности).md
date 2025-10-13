---
sr-due: 2025-10-24
sr-interval: 23
sr-ease: 210
---

#sr-due 
Проверяет - кто делает запрос.
Обрабатывает:
- TLS Client Certificate
- JWT токены
- OpenID Connect
- Webhook Token Auth 
- Anonymous

Без него:
- apiserver не узнает, кто сделал запрос
- не сможет применить авторизацию
- отключение = открытый кластер
[[Authenticator (входная проверка личности)]]
[[Структура внутри apiserver]]