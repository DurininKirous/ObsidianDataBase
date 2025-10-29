---
sr-due: 2025-12-12
sr-interval: 53
sr-ease: 250
---

#sr-due 
- Pod висит в `ContainerCreating`:
    - в Events: `FailedMount: MountVolume.NewMounter...` или `timeout waiting for attach`.
- Причины:
    - драйвер CSI не установлен,
    - проблема в облаке (нет прав создать диск),
    - PV не найден,
    - узел не может смонтировать (например, нет пакета nfs-utils).
[[Ошибки CSI]]
[[CSI]]