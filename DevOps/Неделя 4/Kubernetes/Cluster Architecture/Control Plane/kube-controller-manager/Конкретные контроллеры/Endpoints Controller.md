---
sr-due: 2026-02-02
sr-interval: 80
sr-ease: 230
---

#sr-due 
- **Что делает:**
    - Отслеживает Pod’ы, подходящие под селектор Service.
    - Записывает их IP в объект Endpoints или EndpointSlice.
- **Зачем:** сервисы в Kubernetes — это просто абстракция, реальная маршрутизация строится на основе Endpoints/EndpointSlice.
[[Endpoints Controller]]
[[Конкретные контроллеры]]