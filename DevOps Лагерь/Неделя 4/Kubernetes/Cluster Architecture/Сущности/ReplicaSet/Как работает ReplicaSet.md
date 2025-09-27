---
sr-due: 2025-09-27
sr-interval: 1
sr-ease: 230
---

#sr-due 
- В `.spec.replicas` задаёшь желаемое количество Pod’ов.
- В `.spec.selector` указываешь, какие Pod’ы он контролирует (по label).
- В `.spec.template` задаёшь шаблон Pod’а, который будет запускаться.
 Алгоритм: контроллер в `kube-controller-manager` сравнивает **desired state (реплики в манифесте)** и **current state (Pod’ы в API)** → добавляет или удаляет Pod’ы.
[[Как работает ReplicaSet]]
[[ReplicaSet]]