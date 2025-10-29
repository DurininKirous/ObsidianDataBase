---
sr-due: 2025-11-11
sr-interval: 33
sr-ease: 230
---

#sr-due 
Алгоритм зависит от сигнала, но общие принципы следующие:
1. QoS приоритет:
	1. При Memory/Disk/Pid давлении в первую очередь BestEffort, потом Burstable, потом Guaranteed
2. Внутри класса
	1. MemoryPressure: выше в списке те, кто сильнее превысил свой request по памяти (у BestEffort request=0 → они на вершине)
	2. DiskPressure: ориентир - ephemeral-storage. Больше потребление -> выше шанс эвикции
	3. PIDPressure: у кого больше PID'ов, те кандидаты раньше
3. Приоритет Pod'а также учитывается: менее приоритетные - раньше
4. PDB (_PodDisruptionBudget_) не защищает от эвикций при давлении (это _involuntary disruption_)

>Результат: Pod получает phase `Failed` с reason `Evicted` и сообщением вида:  
`The node was low on resource: memory. Container X was using Y, which exceeds its request Z.`

### Что считается «эпhemeral storage»
- Логи контейнера (`/var/log/containers`, `/var/log/pods`)
- Writable layer образа (copy-on-write)
- `emptyDir` на диске ноды (если не `medium: Memory`)

 Лимитируй это через ресурс **`ephemeral-storage`** (requests/limits), иначе Pod может внезапно вылететь при DiskPressure.
[[Как kubelet выбирает, кого выселять]]
[[QoS и Eviction]]