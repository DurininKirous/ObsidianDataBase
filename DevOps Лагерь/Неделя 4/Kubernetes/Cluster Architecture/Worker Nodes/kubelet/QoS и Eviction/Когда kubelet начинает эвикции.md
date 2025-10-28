---
sr-due: 2025-12-10
sr-interval: 44
sr-ease: 210
---

#sr-due 
Эвикция - вынужденное удаление Pod'ов kubelet'ом при дефиците ресурсов на ноде. Триггеры - сигналы давления:
- `memory.available` ↓ (мало ОЗУ) → `NodeCondition: MemoryPressure=True`
- `nodefs.available` / `imagefs.available` ↓ (мало диска)
- `nodefs.inodesFree` / `imagefs.inodesFree` ↓ (закончились inode)
- `pid.available` ↓ (закончились PID)
Пороговые настройки kubelet:
- **hard**: `--eviction-hard='memory.available<100Mi,...'` → сработает **сразу** при нарушении.
- **soft**: `--eviction-soft=...` + `--eviction-soft-grace-period=...` → сработает **после** выдержки.
- Дополнительно: `--eviction-minimum-reclaim` (сколько ресурса «освободить»),  
    `--eviction-pressure-transition-period` (гистерезис переключений).
CPU **не** вызывает эвикцию (CPU — сжимаемый ресурс), а вот память/диск/PID — да.
[[Когда kubelet начинает эвикции]]
[[QoS и Eviction]]