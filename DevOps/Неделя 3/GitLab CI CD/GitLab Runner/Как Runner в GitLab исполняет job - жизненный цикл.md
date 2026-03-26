---
created: 2026-01-28 19:09
tags:
  - status/seed
  - type/concept
  - domain/gitlab
  - sr-due
sr-due: 2026-09-12
sr-interval: 227
sr-ease: 230
---
### ⚙️ The Why & How
*Инженерная суть. Механика. Зачем это нужно?*
1. GitLab CI CD отдаёт Job в Redis
2. Runner делает `POST /api/v4/jobs/request`
3. GitLab отдаёт Job, если совпадает tag
4. Runner запускает job, и выполняет следующее

pre_clone_script     # подготовка окружения
↓
clone_repo           # git clone проекта
↓
before_script        # если задано
↓
script               # основное тело (например, make docker)
↓
after_script         # всегда выполняется
↓
cleanup / trace / статус → API

---
### 🔗 Connections
- **Родитель**: [[GitLab CI CD]]
