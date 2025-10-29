#sr-due 
Type=simple - дефолт, процесс не форкается

Семантика: systemd считает юнит active сразу после запуска ExecStart=. Никакой дополнительный готовности не ждёт. Когда использовать: обычные демоны/сервисы, которые не уходят в фон и могут стартовать параллельно, готовность не критична или определяется внешне (socket-activation, health-check)

Ключевые директивы: ExecStart=, опц. ExecStartPre/Post=, Restart=, RestartSec=, User=

Подводные камни: если внутри ExecStart скрипт форкается в фон, systemd потеряет главный процесс -> сломанные перезапуски/остановка

Мини-шаблон:
```ini
[Service]
Type=simple
ExecStart=/usr/bin/myapp --fg
Restart=on-failure
```
[[Simple]]
[[Service types]]