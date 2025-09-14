---
sr-due: 2025-09-21
sr-interval: 15
sr-ease: 210
---

#sr-due 
AppArmor - система MAC (Mandatory Access Control), которая:
- ограничивает программы на уровне профилей
В отличие от SELinux, AppArmor привязан к конкретным бинарникам, а не к меткам файлов.
Чаще всего встречается на Ubuntu/Debian.
Когда процесс запускается (например `/usr/sbin/nginx`), ядро смотрит:

- есть ли для этого бинарника профиль в `/etc/apparmor.d/`?
    

Если есть — процесс запускается **«внутри капсулы AppArmor»**, которая:

- разрешает доступ только к тем ресурсам, которые явно описаны в профиле.
    

Если программа попытается сделать что-то не разрешённое:

- в режиме `enforce` — это **блокируется** и пишется в лог.
    
- в режиме `complain` — это **не блокируется**, но записывается предупреждение в лог.

Все профили хранятся в /etc/apparmor.d/
Пример профиля для бинарника:
```
/usr/sbin/nginx {  
  # Разрешить чтение /var/www и всех подкаталогов
  /var/www/** r,

  # Разрешить bind на network socket
  network inet stream,

  # Разрешить чтение общих конфигов
  /etc/nginx/** r,
}
- `r` — read
    
- `w` — write
    
- `x` — execute
    
- `k` — lock
    
- `m` — memory map
```
Применить новые правила:
`systemctl reload apparmor`
## Основная практика

aa-status - покажет какие профили есть, в каком режиме

aa-complain /etc/apparmor.d/usr.sbin.nginx - перевести конкретный профиль в режим "только логировать"

aa-enforce /path/to/profile - вернуть в режим  enforce

aa-disable /path/to/profile - выключить профиль полностью

## Где смотреть логи

tail -f /var/log/syslog | grep DENIED
dmesg | grep apparmor

[[AppArmor]]
[[Неделя 1]]