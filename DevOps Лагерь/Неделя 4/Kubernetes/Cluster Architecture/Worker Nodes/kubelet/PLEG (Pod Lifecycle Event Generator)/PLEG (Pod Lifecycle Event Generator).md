---
sr-due: 2025-11-08
sr-interval: 30
sr-ease: 230
---

#sr-due 
- kubelet нужен "источник правды" о том, что реально происходит с контейнерами
- PLEG переодически опрашивает CRI/рантайм, сравнивает предыдущее состояние с текущим и генерирут события (например, `ContainerStarted`, `ContainerDied`, `PodSandboxRemoved`)
- Эти события подают сигнал воркерам: "состояние изменилось - сделай ещё один SyncPod"
[[PLEG (Pod Lifecycle Event Generator)]]
[[kubelet]]