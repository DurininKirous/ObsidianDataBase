---
sr-due: 2025-10-22
sr-interval: 23
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