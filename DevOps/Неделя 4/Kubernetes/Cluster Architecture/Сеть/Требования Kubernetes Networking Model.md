---
sr-due: 2026-09-26
sr-interval: 209
sr-ease: 230
---

#sr-due 
Kubernetes строго определяет, как должна работать сеть (и CNI плагины обязаны это соблюдать)
1. Pod-to-Pod: любой Pod должен иметь возможность общаться с другим Pod напрямую по Pod IP, без NAT
2. Pod-to-Service: Pod должен уметь обращаться к Service IP, который балансируется на Endpoint'ы
3. Node-to-Pod и Pod-to-Node: любой Pod может общаться с нодой и наоборот
Это делает сеть плоской и предсказуемой, без хаоса NAT
[[Требования Kubernetes Networking Model]]
[[Сеть]]