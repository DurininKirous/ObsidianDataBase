---
sr-due: 2026-04-05
sr-interval: 87
sr-ease: 230
---

#sr-due 
**Ключевое:** объединяет **lowerdir**(ы) read-only и **upperdir** (rw) → быстрые копии образов, copy-up на запись.

**Где уместна:** Docker/Podman (overlay2), быстрые «ветки» окружений.

**Подводные камни:**
- Не все FS одинаково хороши под upper/work (обычно ext4/xfs).
- Inotify/атрибуты/особые фичи иногда ведут себя нетривиально (зависит от ядра).
[[Obsidian Vault/Rebrain/Studying/Linux Internals/Файловые системы/Типы файловых систем/overlayfs|overlayfs]]
[[Типы файловых систем]]