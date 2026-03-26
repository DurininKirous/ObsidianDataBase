---
sr-due: 2026-07-31
sr-interval: 177
sr-ease: 230
---

#sr-due 
- Режимы:
    - **none** (по умолчанию): CPU распределяются cgroupsами динамически.
    - **static**: kubelet закрепляет целые CPU (CPU pinning) для контейнеров с `Guaranteed QoS` и `requests == limits`.
- Используется для low-latency приложений, DPDK, ML-инференса.
- Включается:
	cpuManagerPolicy: static
	cpuManagerReconcilePeriod: 5s
	
При этом kubelet реально делает `sched_setaffinity` для контейнеров.
[[CPU Manager]]
[[Ресурсные менеджеры]]