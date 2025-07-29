---
sr-due: 2025-08-20
sr-interval: 23
sr-ease: 250
---

#sr-due 
pivot_root - системный вызов для замены корня файловой системы.
`int pivot_root(const char *new_root, const char *put_old);`

### Назначение
Полностью заменить текущий / на new_root, а старый корень переместить в put_old - поддиректорию в new_root

### Как работает
- В процессе должен быть mount namespace 
- Монтируем новую файловую систему 
- Создаём в ней папку put_old
- Вызываем pivot_root(new_root, put_old)
- Теперь:
	new_root становится /
	put_old доступен по /put_old
- Обычно затем:
	umount /put_old

### Требования
- new_root и put_old должны быть на одном mount point
- put_old должен быть каталогом внутри new_root, не подмонтированным
- нужны права cap_sys_admin
- обычно используется только внутри mount namespace, чтобы не повредить хост-систему




[[Pivot_root]]
[[Linux Primitives]]