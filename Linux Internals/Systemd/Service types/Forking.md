---
sr-due: 2025-12-29
sr-interval: 35
sr-ease: 230
---

#sr-due 
Type=forking - демон сам делает fork() (daemon mode)

Семантика: считается запущенным, когда дочерний процесс отделился. Обычно требуется файл с PID.

Когда использовать: старые демоны, которые обязательно демонизируются сами (Apache httpd в legacy-режиме)

Ключевые директивы: PIDFile= (очень желательно), ExecStart=, ExecReload=, ExecStop=, Restart=

Подводные камни: без корректного PIDFile= systemd не узнает $MAINPID; прерывистые гонки при раннем чтении PID-файла; лучше перевести такие демоны в режим foreground и уйти на simple/notify

Мини-шаблон:
```ini
[Service]
Type=forking
PIDFile=/run/myapp.pid
ExecStart=/usr/sbin/myapp -D    # запускается и форкается
Restart=on-failure
```
[[Forking]]
[[Service types]]