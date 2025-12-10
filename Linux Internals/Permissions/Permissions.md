---
sr-due: 2025-12-17
sr-interval: 27
sr-ease: 230
---

#sr-due 
## Разбор `ls -l`
Пример: `-rwxr-xr-- 1 user group 4096 Oct 28 10:00 file.txt`
- **1-й символ**: тип (`-` файл, `d` каталог, `l` симлинк, `c/b` устройства, `p` FIFO, `s` сокет).
- **Дальше 9 символов**: права **owner / group / others**: `r=4, w=2, x=1`.  
    `rwx`=7, `r-x`=5, `r--`=4, `-wx`=3, `--x`=1 и т.д.

## Числовые права (octal)
- `755` → `rwx r-x r-x` (owner=7, group=5, others=5).
- `644` → `rw- r-- r--` (часто для обычных файлов).  
    Команды:	
```
chmod 755 script.sh         # числом
chmod u=rwx,go=rx script.sh # символически
```
[[Permissions]]
[[Linux Internals]]