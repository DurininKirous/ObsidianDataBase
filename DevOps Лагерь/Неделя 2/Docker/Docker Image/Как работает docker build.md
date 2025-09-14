---
sr-due: 2025-11-19
sr-interval: 74
sr-ease: 246
---

#sr-due 
- Читает Dockerfile построчно
- Каждый `RUN`, `COPY`, `ADD` ➝ создаёт слой
- Кэширует слои, если шаги не изменились
- Создаёт манифест + config + записывает в content store
[[Как работает docker build]]
[[Docker Image]]