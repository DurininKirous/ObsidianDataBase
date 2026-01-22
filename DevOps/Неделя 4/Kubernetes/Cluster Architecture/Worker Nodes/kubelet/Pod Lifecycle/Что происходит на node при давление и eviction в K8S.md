---
created: 2026-01-18 08:09
tags:
  - status/seed
  - type/concept
  - domain/linux
  - sr-due
sr-due: 2026-06-29
sr-interval: 162
sr-ease: 230
---
### 💡 The What
*Что это?*
При чрезмерном расходовании ресурсов на node kubelet может начать запуск процесса выселения Pod'ов с нод

### ⚙️ The Why & How
*Инженерная суть. Механика. Зачем это нужно?*
- При MemoryPressure/DiskPressure/PIDPressure [[kubelet]] запускает eviction manager ([[QoS и Eviction]]):
	- Сначала BestEffort, затем Burstable, затем Guaranteed
- Эвикция = "вежливое" удаление: Pod запускает SIGTERM, и создаётся на другой node

---
### ⚔️ VS / Trade-offs
*С чем сравнить? Плюсы/Минусы.*
- **VS [[OOM Killer]]**: В случае OOM контейнер может удалиться, в случае eviction весь Pod удаляется из ноды и переносится в другое место. 
- **Trade-off**: 


---
### 🔗 Connections
- **Родитель**: [[QoS и Eviction]]
- **Влияет на**: [[Rate limits on eviction]], [[Pod Lifecycle]], [[Завершение Pod]]
- **Инсайт**: Стоит такие ситуации предусматривать через QoS и [[PodDisruptionBudget]]
