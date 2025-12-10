---
sr-due: 2025-12-24
sr-interval: 40
sr-ease: 230
---

#sr-due 
Вариант 1: Software LB (NGINX, HAProxy)
[NGINX] -> Server 1, Server 2, Server 3

Плюсы: Дешёвый, гибкий, можно настроить что угодно
Минусы: Сам LB - это SPOF! (нужен failover)

Решение: Два LB + Keepalived (Виртуальный IP переключается при сбое)

---

Вариант 2: Cloud Scaling Balancer (AWS ELB, GCP Load Balancer)
[AWS ALB] -> Auto Scaling Group (Server 1-10)

Плюсы: Managed (AWS сам обеспечивает HA), auto-scaling, интеграция
Минусы: Дороже, меньше контроля

---

Вариант 3: DNS Load Balancing
example.com -> 1.2.3.4, 1.2.3.5, 1.2.3.6

DNS возвращает несколько IP, клиент сам выбирает

Плюсы: очень дешёвый
Минусы: 
- Нет health checks (если сервер упал, DNS всё равно вернёт его IP)
- TTL кеширование (клиент может кешировать "мёртвый" IP)

Когда использовать: Geo-routing (Клиент из Европы -> EU datacenter)
[[Где размещать Load Balancer]]
[[Load Balancer]]