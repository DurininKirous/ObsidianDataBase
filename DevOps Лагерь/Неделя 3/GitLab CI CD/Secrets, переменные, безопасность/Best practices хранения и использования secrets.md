---
sr-due: 2025-11-09
sr-interval: 61
sr-ease: 270
---

#sr-due 
✅ Делай:
- все ключи → в UI `Settings → CI/CD → Variables`;
- `masked + protected`;
- `file:` для ключей, конфигов, сертификатов;
- доступ к переменным — только для production-веток.

❌ Не делай:
- `TOKEN=abc123` в `.gitlab-ci.yml`;
- не вставляй секреты в `script:` напрямую;
- не логируй переменные без маскировки (`echo $TOKEN` в логе = утечка).
[[Best practices хранения и использования secrets]]
[[Secrets, переменные, безопасность]]