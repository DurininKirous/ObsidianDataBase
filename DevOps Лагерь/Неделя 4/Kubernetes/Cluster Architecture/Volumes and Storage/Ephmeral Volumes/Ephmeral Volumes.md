---
sr-due: 2025-09-29
sr-interval: 2
sr-ease: 230
---

#sr-due 
 ### Зачем нужны
 - Данные в контейнере живут в слое overlayFS и исчезают при удалении Pod'а
 - Иногда нужны временные данные: кэш, буферы, обмен файлами между контейнерами
 - Для этого Kubernetes даёт ephmeral volumes. Они живут только пока живёт Pod
[[Ephmeral Volumes]]
[[Volumes and Storage]]