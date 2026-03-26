---
created: 2026-01-28 17:45
tags:
  - status/seed
  - type/concept
  - domain/docker
  - sr-due
sr-due: 2026-08-17
sr-interval: 201
sr-ease: 230
---
### ⚙️ The Why & How
*Инженерная суть. Механика. Зачем это нужно?*
Когда запускается новый контейнер, например:
`docker run -it alpine sh`
Docker:
1. Создаёт новый [[Namespaces]] через clone или через [[runc]]
2. Монтирует [[DevOps/Неделя 2/Linux primitives/overlayFS/overlayFS|overlayFS]] в новом mount namespace [[Типы namespaces]]
3. Подключает к Docker bridge в новом net namespace [[Docker Network]]

---
### 🔗 Connections
- **Родитель**: [[Docker]]
