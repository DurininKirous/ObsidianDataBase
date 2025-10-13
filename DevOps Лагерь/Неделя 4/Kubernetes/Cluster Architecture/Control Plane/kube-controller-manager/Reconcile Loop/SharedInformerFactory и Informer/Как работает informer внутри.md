---
sr-due: 2025-10-19
sr-interval: 16
sr-ease: 190
---

#sr-due 
API Server
   ↓
ListWatch
   ↓
Reflector
   ↓
DeltaFIFO (очередь изменений)
   ↓
Processor (обработка)
   ↓
EventHandler (AddFunc, UpdateFunc, DeleteFunc)
   ↓
enqueue → WorkQueue


Компоненты:

| Компонент     | Назначение                                                                                 |     |
| ------------- | ------------------------------------------------------------------------------------------ | --- |
| `ListWatch`   | Указывает, как получать данные (`List()` для начальной загрузки, `Watch()` для обновлений) |     |
| `Reflector`   | Объект, который подписывается на `ListWatch` и следит за изменениями                       |     |
| `cache.Store` | Локальный кеш ресурсов (в памяти)                                                          |     |
| `DeltaFIFO`   | Очередь изменений (`Add`, `Update`, `Delete`)                                              |     |
| `Processor`   | Обрабатывает события и вызывает `AddFunc`, `UpdateFunc`, `DeleteFunc`                      |     |
## Пример работы:
1. `Reflector` делает `List()` всех Pod’ов → заполняет кеш
2. Затем запускает `Watch()` → слушает новые события
3. Все изменения кладутся в `DeltaFIFO`
4. Информер читает их из очереди → вызывает нужный handler
[[Как работает informer внутри]]
[[SharedInformerFactory и Informer]]