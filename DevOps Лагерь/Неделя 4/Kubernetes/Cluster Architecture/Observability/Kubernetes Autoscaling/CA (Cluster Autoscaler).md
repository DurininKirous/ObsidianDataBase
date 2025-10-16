---
sr-due: 2025-10-21
sr-interval: 5
sr-ease: 230
---

#sr-due 
### Где живёт
Отдельный Deployment (не часть control-plane), работает через Cloud Provider API.
### Что делает
- Следит за pending-подами (не помещаются ни на одну ноду).
- Увеличивает кластер (ScaleUp) → добавляет ноды (через API облака / autoscaling group).
- Удаляет ноды (ScaleDown), если они:
    - idle;
    - не держат системные поды;
    - их поды можно переселить.

### Алгоритм
1. Каждые N секунд CA смотрит scheduler cache:
    - Pending pods?
    - Utilization < threshold?
2. Вызывает **NodeGroup.CloudProvider** → AddNode() / DeleteNode().
3. kube-scheduler назначает pending поды на новые ноды.

### Особенности
- Требует labels/taints `cluster-autoscaler.kubernetes.io/safe-to-evict`.
- Работает совместно с HPA:  
    HPA увеличивает поды → PodPending → CA добавляет ноды.
[[CA (Cluster Autoscaler)]]
[[Kubernetes Autoscaling]]