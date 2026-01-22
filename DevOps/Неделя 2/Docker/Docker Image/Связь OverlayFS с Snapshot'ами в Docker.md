---
created: 2026-01-05 03:53
tags:
  - status/seed
  - type/concept
  - domain/linux
  - sr-due
sr-due: 2026-05-27
sr-interval: 142
sr-ease: 206
---
### 💡 The What
*Что это?*
OverlayFS напрямую связан с Snapshot'ами и образами Docker да и в целом контейнеризацией
### ⚙️ The Why & How
*Инженерная суть. Механика. Зачем это нужно?*
Когда запускается контейнер:
- Все read-only слои -> lowerdir
- Создаётся read-write [[Snapshot]] -> upperdir (diff/)
- [[ObsidianDataBase/DevOps/Неделя 2/Linux primitives/overlayFS/overlayFS|overlayFS]] объединяет всё: `mount -t overlay overlay -o lowerdir=sl3:sl2:sl1,upperdir=diff/,workdir=work/ merged/`
merged - rootFS контейнера
diff - изменения, которые были записаны контейнером
lowerdir - изначальные слои, не модифицируется
### ⚔️ VS / Trade-offs
*С чем сравнить? Плюсы/Минусы.*
- **VS [[Btrfs]], [[ext4]], [[XFS]]**: Более лучшая обработка больших файлов, скорость чтения-записи, но огромная трата ресурсов диска 
- **Trade-off**: 
	- Плюсы: Экономия памяти
	- Минусы: Медленная запись больших файлов

---
### 🔗 Connections
- **Родитель**: [[ObsidianDataBase/DevOps/Неделя 2/Linux primitives/overlayFS/overlayFS|overlayFS]], [[ObsidianDataBase/Linux Internals/Файловые системы/Типы файловых систем/overlayfs|overlayfs]]
- **Влияет на**: [[Docker Image]], [[Как Docker использует overlayFS]]
- **Инсайт**: 
