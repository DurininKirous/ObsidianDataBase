---
sr-due: 2025-12-15
sr-interval: 28
sr-ease: 230
---

#sr-due 
Helm - менеджер релизов для Kubernetes.
Он делает три вещи:
1. Пакует манифесты в chart (архив пакета)
2. Рендерит шаблоны (go-templates) в обычные yaml
3. Оркестрирует релиз: применяет YAML в кластер, хранит историю, позволяет upgrade/rollout
[[Helm]]
[[Kubernetes]]