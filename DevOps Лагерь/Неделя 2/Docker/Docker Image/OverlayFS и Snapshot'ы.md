---
sr-due: 2025-08-18
sr-interval: 21
sr-ease: 226
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