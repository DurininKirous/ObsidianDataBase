---
sr-due: 2025-11-12
sr-interval: 34
sr-ease: 230
---

#sr-due 
- **Что делает:**
    - Отслеживает Pod’ы, подходящие под селектор Service.
    - Записывает их IP в объект Endpoints или EndpointSlice.
- **Зачем:** сервисы в Kubernetes — это просто абстракция, реальная маршрутизация строится на основе Endpoints/EndpointSlice.
[[Endpoints Controller]]
[[Конкретные контроллеры]]