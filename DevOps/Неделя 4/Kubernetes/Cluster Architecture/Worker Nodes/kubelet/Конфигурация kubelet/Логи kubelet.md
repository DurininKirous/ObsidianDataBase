---
sr-due: 2026-06-28
sr-interval: 171
sr-ease: 250
---

#sr-due 
kubelet — системный сервис (systemd).
Смотреть через:
	journalctl -u kubelet -f
- Основные категории логов:
    - **Scheduling на ноде**: `SyncPod`, `PLEG`.
    - **Проблемы сети**: `CNI failed to assign IP`.
    - **Сторадж**: `MountVolume.NewMounter...`
    - **Эвикции**: `eviction manager: pods evicted`
    - **GC**: `image gc` / `container gc`.
Это первое место при `ContainerCreating`, `Evicted`, `CrashLoopBackOff`.
[[Логи kubelet]]
[[Конфигурация kubelet]]