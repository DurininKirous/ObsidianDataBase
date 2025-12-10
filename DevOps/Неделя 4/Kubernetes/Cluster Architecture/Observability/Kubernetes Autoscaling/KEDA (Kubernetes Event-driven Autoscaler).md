---
sr-due: 2026-02-08
sr-interval: 68
sr-ease: 230
---

#sr-due 
### Суть
Автоскейлинг на **внешние события** (не только CPU/Memory):  
очереди, базы, webhooks, Prometheus, Kafka, Redis, RabbitMQ, Azure Monitor и т. д.
### Архитектура
```scss
ScaledObject (CRD)
 ├─ Scaler (адаптер к источнику: Prometheus, RabbitMQ, Kafka, etc.)
 ├─ Metrics Adapter (реализует external.metrics.k8s.io)
 └─ KEDA Operator (выпускает/удаляет HPA)
```
### Как работает
1. Scaler получает метрики (например, длину очереди).
2. Отдаёт их через **external.metrics.k8s.io** (KEDA adapter).
3. KEDA Operator динамически создаёт/обновляет HPA для Deployment.
4. HPA масштабирует поды на основе этих метрик.

Пример:
```yaml
apiVersion: keda.sh/v1alpha1
kind: ScaledObject
metadata:
  name: queue-scaler
spec:
  scaleTargetRef:
    name: worker
  minReplicaCount: 1
  maxReplicaCount: 20
  triggers:
  - type: rabbitmq
    metadata:
      queueName: tasks
      host: RabbitMqConnectionString
      queueLength: "100"
```
[[KEDA (Kubernetes Event-driven Autoscaler)]]
[[Kubernetes Autoscaling]]