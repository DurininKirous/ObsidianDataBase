---
sr-due: 2025-07-30
sr-interval: 9
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