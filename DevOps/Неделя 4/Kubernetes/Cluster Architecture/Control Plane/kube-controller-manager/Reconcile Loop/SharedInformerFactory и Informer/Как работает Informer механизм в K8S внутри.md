---
created: 2026-01-17 11:10
tags:
  - status/seed
  - type/concept
  - domain/k8s
  - sr-due
sr-due: 2026-05-04
sr-interval: 107
sr-ease: 190
---
### 💡 The What
*Что это?*
Informer состоит из набора разных компонентов, каждый выполняет свою отдельную функцию

### ⚙️ The Why & How
*Инженерная суть. Механика. Зачем это нужно?*
[[kube-apiserver]]
   ↓
[[ListWatch]]
   ↓
[[Reflector в Informer в K8S]]
   ↓
[[DeltaFIFO]] (очередь изменений)
   ↓
[[Processor]] (обработка)
   ↓
[[EventHandlerFuncs]] (AddFunc, UpdateFunc, DeleteFunc)
   ↓
[[Enqueue (добавление в очередь)]] → [[WorkQueue]]

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

---
### ⚔️ VS / Trade-offs
*С чем сравнить? Плюсы/Минусы.*
- **VS [[...]]**: 
- **Trade-off**: 


---
### 🔗 Connections
- **Родитель**: [[SharedInformerFactory и Informer]]
- **Влияет на**: [[kube-controller-manager]]
- **Инсайт**: 
