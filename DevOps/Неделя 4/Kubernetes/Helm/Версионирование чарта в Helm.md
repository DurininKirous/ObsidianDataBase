---
created: 2026-01-28 19:12
tags:
  - status/seed
  - type/concept
  - domain/linux
  - sr-due
sr-due: 2026-05-29
sr-interval: 82
sr-ease: 210
---
### ⚙️ The Why & How
*Инженерная суть. Механика. Зачем это нужно?*
- `version` в `Chart.yaml` — версия **чарта** (semver, влияет на репозиторий чарта).
- `appVersion` — версия **приложения** (для информации, можно выводить в шаблонах/лейблах).
- В OCI/репо релиз идентифицируешь по `chart@version`, а в кластере — по `release-name + revision`.

---
### 🔗 Connections
- **Родитель**: [[Helm]]
- **Влияет на**: [[Что происходит при helm install]]
- **Инсайт**: Версия приложения != версия чарта, при обновлении чарта Grafana ловился на этом
