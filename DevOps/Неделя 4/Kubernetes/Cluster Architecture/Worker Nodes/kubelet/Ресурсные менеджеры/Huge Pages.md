---
sr-due: 2026-02-18
sr-interval: 101
sr-ease: 250
---

#sr-due 
- Linux может выделять **большие страницы** (2MB, 1GB).
- Используется для баз данных, ML, HPC.
- В Pod можно запросить:
	resources:
	  requests:
		    hugepages-2Mi: 1Gi
  limits:
		    hugepages-2Mi: 1Gi
kubelet пробросит контейнеру доступ к hugepages.

[[Huge Pages]]
[[Ресурсные менеджеры]]