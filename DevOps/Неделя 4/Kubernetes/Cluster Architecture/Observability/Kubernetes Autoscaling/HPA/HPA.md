---
sr-due: 2026-02-06
sr-interval: 66
sr-ease: 230
---

#sr-due 
HPA - Horizontal Pod Autoscaler.
Где живёт:  
	В kube-contoller-manager как отдельный контроллер

Как работает по шагам:
1. Каждые `--horizontal-pod-autoscaler-sync-period` (по умолчанию 15 секунд):
	1. получает список HPA из API с помощью etcd
	2. по каждому HPA - смотрит targetRef (Deployment/RS/StatefulSet)
	3. запрашивает метрики через Metrics API (metrics.k8s.io, custom.metrics.k8s.io, external.metrics.k8s.io)
2. Для каждой метрики считает:
	1. desiredReplicas = currentReplicas * (currentMetric / targetMetric)
3. Нормализует результат (округление, upscale / downscale policies)
4. Пишет PATCH на .spec.replicas целевого объекта (Scale subresources)
5. Публикует Events в API (kubectl describe hpa -> видно всё)
[[HPA]]
[[Kubernetes Autoscaling]]