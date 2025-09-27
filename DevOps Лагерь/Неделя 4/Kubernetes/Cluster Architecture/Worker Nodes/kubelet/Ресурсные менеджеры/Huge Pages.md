---
sr-due: 2025-10-08
sr-interval: 13
sr-ease: 230
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