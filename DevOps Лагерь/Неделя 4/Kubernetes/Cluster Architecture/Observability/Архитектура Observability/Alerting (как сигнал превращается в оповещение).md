---
sr-due: 2025-10-21
sr-interval: 5
sr-ease: 230
---

- Prometheus rules: выражения в PromQL -> состояние ALERT (firing/resolve)
- Alertmanager: routing (по лейблам: severity, team), inhibition (не спаммить при корневом инциденте), silences (временные mute)
- Каналы: Telegram/Slack/Email/Webhook
- Политики: warning/critical, playbook ссылкой в аннотациях
Хорошие практики:
- алёртить по симптомам (SLO error rate), а не по всем внутренностям
- "group by service/team" - чтобы не заливать всех
- auto-remediation триггеры (внешние вебхуки/оркестраторы)
[[Alerting (как сигнал превращается в оповещение)]]
[[Архитектура Observability в Kubernetes]]