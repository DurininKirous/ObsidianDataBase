---
sr-due: 2025-11-29
sr-interval: 42
sr-ease: 210
---

#sr-due 
Тут происходит следующее:
if deployment.spec.replicas != currentReplicaCount {
    // нужно больше/меньше pod'ов → создать/удалить ReplicaSet или Pod
}
if templateHasChanged() {
    // начать rolling update
}
if pod.Status == CrashLoopBackOff {
    // записать event или пересоздать
}

Каждая реализация контроллера пишет свою логику. Но структура одинакова:
- получаем текущее состояние
- сравниваем с желаемым
- вызываем действия
[[Reconcile Logic]]
[[Reconcile Loop (контроллерный цикл)]]