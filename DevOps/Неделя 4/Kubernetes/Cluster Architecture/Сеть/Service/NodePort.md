---
sr-due: 2025-11-26
sr-interval: 39
sr-ease: 230
---

#sr-due 
- На каждой ноде слушает `nodeIp:nodePort`
- Путь:
	- Вход снаружи: `Client -> NodeIP:nodePort -> (внутри ноды) VIP -> DNAT -> PodIP`
- externalTrafficPolicy:
	- Cluster (дефолт): нода может переслать трафик на любой Pod в кластере (SNAT возможен -> клиентский IP теряется)
	- Local: трафик принимают только ноды с локальным endpoint; сохраняется исходный IP клиента. На нодах без локального endpoint трафик будет отброшен
[[NodePort]] 
[[Obsidian Vault/Rebrain/Studying/DevOps/Неделя 4/Kubernetes/Cluster Architecture/Сеть/Service/Service]]