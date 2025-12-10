---
sr-due: 2026-05-29
sr-interval: 190
sr-ease: 250
---
	
#sr-due 
Snapshot - слой файловой системы
- может быть read-only
- может быть read-write
Используется через overlayFS:
- lowerdir - слои образа
- upperdir - директория с изменениями
- workdir - служебная директория
rootFS монтируется как результат overlay и передаётся runc

[[Snapshot]]
[[containerd]]