---
sr-due: 2025-08-18
sr-interval: 21
sr-ease: 246
---

#sr-due 
- Читает Dockerfile построчно
- Каждый `RUN`, `COPY`, `ADD` ➝ создаёт слой
- Кэширует слои, если шаги не изменились
- Создаёт манифест + config + записывает в content store
[[Как работает docker build]]
[[Docker Image]]