---
sr-due: 2025-10-06
sr-interval: 15
sr-ease: 228
---

#sr-due 
generation:
- Это число в metadata.generation, которое увеличивается каждый раз, когда изменяется spec объекта
- Автоматически поддерживается API-сервером
- Если меняешь только status, generation не меняется
observedGeneration:
- Это поле в .status.observedGeneration, которое обновляет контроллер, когда он обработал изменения в spec
- Контроллер говорит: "Я видел generation=X и уже обработал его"
[[Generation and observedGeneration]]
[[Reconcile Loop (контроллерный цикл)]]