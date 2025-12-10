---
sr-due: 2026-01-25
sr-interval: 60
sr-ease: 230
---

#sr-due 
VPA - Vertical Pod Autoscaling
Автоматически подбирает CPU/Memory requests/limits для контейнеров, на основе фактического использования

Компоненты (3 штуки):
VPA CRD (описание политики)
 ├─ Recommender → анализирует usage-history из metrics API / Prometheus
 ├─ Updater → удаляет и пересоздаёт поды (если разрешено)
 └─ Admission Controller → изменяет PodSpec на старте (mutating webhook)

### Где берёт данные
- Метрики usage с kubelet (через metrics-server / Prometheus adapter).
- Хранит историю в CRD `VerticalPodAutoscalerCheckpoint`.
### Минусы
- Не дружит с HPA (оба меняют ресурсы — разная ось).
- Пересоздаёт поды → short downtime.
- Рекомендуется для **бэкграунд** сервисов, не для latency-sensitive.
[[VPA]]
[[Kubernetes Autoscaling]]