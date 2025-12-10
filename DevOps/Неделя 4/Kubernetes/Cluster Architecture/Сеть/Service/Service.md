---
sr-due: 2026-02-10
sr-interval: 83
sr-ease: 230
---

#sr-due 
### Зачем он нужен
- Pod IP нестабилен: Pod пересоздался -> IP поменялся
- Нужна устойчивая точка входа, которая балансирует на актуальные Pod'ы

### Что такое Service
- Объект API, дающий:
	- Стабильный виртуальный IP (VIP, ClusterIP)
	- DNS-имя в кластерной зоне,
	- Прокси балансировку трафика к наборам Pod'ов (выбор по spec.selector)

### Как Service находит Pod'ы
- По `spec.selector` выбираются Pod'ы -> контроллер control plane создаёт/обновляет EndpointSlice(ы) - список адресов конечных точек: PodIP:targetPort, плюс метаданные (готовность, зона/нода, подсказки локальности)
> Важно: Pod с `readinessProbe = false` исключается из EndpointSlice -> не получает трафик из Service

[[Obsidian Vault/Rebrain/Studying/DevOps/Неделя 4/Kubernetes/Cluster Architecture/Сеть/Service/Service]]
[[Сеть]]