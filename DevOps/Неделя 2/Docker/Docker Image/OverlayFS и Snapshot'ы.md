---
sr-due: 2025-12-10
sr-interval: 56
sr-ease: 206
---

#sr-due 
Когда запускается контейнер:
1. Все read-only слои -> lowerdir
2. Создаётся rw snapshot -> upperdir (diff/)
3. OverlayFS объединяет всё:
mount -t overlay overlay -o lowerdir=sl3:sl2:sl1,upperdir=diff/,workdir=work/ merged/

merged/ - rootFS контейнера
В diff/ пишутся изменения
lowerdir не модифицируется


[[OverlayFS и Snapshot'ы]]
[[Docker Image]]