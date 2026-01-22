---
created: 2026-01-06 15:58
tags:
  - status/seed
  - type/concept
  - domain/k8s
  - sr-due
sr-due: 2026-05-07
sr-interval: 121
sr-ease: 210
---
### 💡 The What
*Что это?*
Эвикция - вынужденное удаление Pod'ов kubelet'ом при дефиците ресурсов на ноде. Триггеры - сигналы давления

### ⚙️ The Why & How
*Инженерная суть. Механика. Зачем это нужно?*
Тригеры:
- `memory.available` ↓ (мало ОЗУ) → `NodeCondition: MemoryPressure=True`
- `nodefs.available` / `imagefs.available` ↓ (мало диска)
- `nodefs.inodesFree` / `imagefs.inodesFree` ↓ (закончились inode)
- `pid.available` ↓ (закончились PID)
Пороговые настройки [[kubelet]]:
- **hard**: `--eviction-hard='memory.available<100Mi,...'` → сработает **сразу** при нарушении.
- **soft**: `--eviction-soft=...` + `--eviction-soft-grace-period=...` → сработает **после** выдержки.
- Дополнительно: `--eviction-minimum-reclaim` (сколько ресурса «освободить»),`--eviction-pressure-transition-period` (гистерезис переключений).
CPU **не** вызывает эвикцию (CPU — сжимаемый ресурс), а вот память/диск/PID — да.

---
### ⚔️ VS / Trade-offs
*С чем сравнить? Плюсы/Минусы.*
- **VS [[OOM Killer]]**: OOM убьёт контейнер внутри пода из-за нехватки ресурсов и тот с большой вероятностью будет создан снова, эвикция уже полностью выселит под.
- **Trade-off**: 
	- Плюсы: экономия ресурсов
	- Минусы: без правильной обработки эвикций можно остаться без работающих инсталяций сервисов. [[PodDisruptionBudget]]

---
### 🔗 Connections
- **Родитель**: [[QoS и Eviction]]
- **Влияет на**: [[Rate limits on eviction]]
- **Инсайт**: Стоит тщательно учитывать сценарии отработки Eviction, чтобы не остаться без сервисов нужных
