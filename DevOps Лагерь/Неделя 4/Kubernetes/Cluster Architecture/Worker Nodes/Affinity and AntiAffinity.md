---
sr-due: 2025-10-20
sr-interval: 2
sr-ease: 210
---

#sr-due 
nodeAffinity:
Affinity расширяет nodeSelector:
- `requiredDuringSchedulingIgnoredDuringExecution` — _жёсткое_ правило (обязательно)
- `preferredDuringSchedulingIgnoredDuringExecution` — _мягкое_ (балл приоритета, можно нарушить)

podAffinity / podAntiAffinity:
Оперируют не нодами, а соседями-подами.
Можно группировать поды одного типа вместе (Affinity) или наоборот - разносить (AntiAffinity).
Пример — не больше одной реплики на хост:
```yaml
affinity:
  podAntiAffinity:
    requiredDuringSchedulingIgnoredDuringExecution:
    - labelSelector:
        matchExpressions:
        - key: app
          operator: In
          values: ["nginx"]
      topologyKey: kubernetes.io/hostname
```
Планировщик смотрит, где уже запущены такие поды, и старается не ставить новый рядом.

#### **topologySpreadConstraints**
Современная альтернатива anti-affinity (работает быстрее).  
Позволяет задать равномерное распределение по ключу (zone, hostname и т.д.).
[[Affinity and AntiAffinity]]
[[Worker Nodes]]