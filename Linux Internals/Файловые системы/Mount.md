---
sr-due: 2025-12-25
sr-interval: 32
sr-ease: 230
---

#sr-due 
Базовый синтаксис:
```bash
sudo mount -t <fstype> <source> <target> [ -o opt1,opt2,... ]
sudo umount <target|source>
```
Примеры:
```bash
sudo mount -t ext4 /dev/sda2 /home
sudo mount -t nfs server:/export /mnt
sudo mount -t tmpfs -o size=2G,mode=1777 tmpfs /tmp
```

Текущие маунты: 
```bash
findmnt                          # лучшее человекочитаемое дерево маунтов
findmnt -t ext4,xfs,nfs          # фильтр по типам
cat /proc/self/mounts            # «истина» из ядра
mount | column -t                # совместимый вывод (чуть менее точный)
```

# Ключевые опции (по смысловым группам)

## Безопасность (часто для `/tmp`, внешних томов, bind-маунтов)
- `noexec` — нельзя исполнять бинарники **из этой ФС** (скрипт всё ещё можно запустить через интерпретатор).
- `nosuid` — игнорировать SUID/SGID биты.
- `nodev` — игнорировать спецфайлы устройств.
- `ro` / `rw` — только чтение / чтение-запись.
- `uid=`, `gid=`, `umask=`, `fmask=`, `dmask=` — права/владение на **не-POSIX** ФС (vfat/exfat, cifs).

## Производительность / ресурс
- `noatime` / `relatime` — уменьшить записи `atime`.
- `discard` — онлайн-TRIM (для SSD; часто лучше периодический `fstrim`).
- `compress=...` — сжатие на btrfs (`zstd`, `zlib`, `lzo`).
- FS-специфичные: `xfs`: `inode64`; `ext4`: `data=ordered|journal|writeback`, `commit=5`.

## Поведение / надёжность
- `errors=remount-ro` (ext4) — при ошибке переключить том в `ro`.
- `_netdev` — помечает ФС как «сетевую» (важно для порядка старта/останова).
- `nofail` — не падать при загрузке, если маунт не удался.

## systemd-расширения из fstab
- `x-systemd.automount` — ленивый автомаунт (смонтирует по первому доступу).
- `x-systemd.idle-timeout=60s` — авто-unmount при простое.
- `x-systemd.requires=` / `x-systemd.after=` — зависимости как у юнитов.


### Особые режимы `mount`
1) **Remount** — сменить опции «на лету»
```bash
sudo mount -o remount,rw /
sudo mount -o remount,noexec,nosuid,nodev /tmp
```
2) **Bind / rbind** — отобразить каталог в другое место
```bash
sudo mount --bind /var/lib/app/data /srv/data
# read-only bind = двойной ремоунт:
sudo mount -o remount,bind,ro /srv/data
# рекурсивно (включая вложенные маунты):
sudo mount --rbind /var/lib/app /srv/app
```
3) **Loop** — монтировать файл как диск
```bash
truncate -s 1G disk.img
mkfs.ext4 disk.img
sudo mount -o loop disk.img /mnt/loop
# (или losetup -fP disk.img; mount /dev/loopX /mnt/loop)
```
4) **Move** — переехать с одной точки на другую без отмонтирования
```bash
sudo mount --move /old/mnt /new/mnt
```
5) **Propagation** — распространение маунтов между namespace’ами
```bash
# сделать точку приватной/общей/сломленной/разделяемой
sudo mount --make-private  /mnt
sudo mount --make-shared   /mnt
sudo mount --make-slave    /mnt
sudo mount --make-rshared  /
```

# Типы источников (что монтируем)
- **Локальные блочные устройства**: `/dev/sdXN`, `/dev/nvme*n*`, LVM (`/dev/mapper/...`), mdraid.
- **Виртуальные ФС**: `proc`, `sysfs`, `tmpfs`, `cgroup2`, `bpf`, `devpts`.
- **Сетевые**: `nfs`, `cifs` (SMB). Для них действуют «хелперы» `mount.nfs`, `mount.cifs` (опции специфичны).
- **Union/контейнерные**: `overlay` (`lowerdir`, `upperdir`, `workdir`).
[[Obsidian Vault/Rebrain/Studying/Linux Internals/Файловые системы/Mount|Mount]]
[[Файловые системы]]