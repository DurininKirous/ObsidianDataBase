---
sr-due: 2025-12-30
sr-interval: 36
sr-ease: 230
---

#sr-due 
Type=notify - процесс сам уведомляет systemd, когда готов

Семантика: юнит становится active, только когда процесс пошлёт READY=1 через sd_notify (AF_UNIX сокет $NOTIFY_SOCKET).

Когда использовать: сервера, которым нужно время на инициализацию (открыть порт, прогреть кеш), и важно сообщить реальную готовность перед зависимыми юнитами.

Ключевые директивы: Type=notify, опц. NotifyAccess=main|all (если уведомляет не только главный PID)

Подводные камни: трубется линковка с libsystemd или использование совместимых обёрток; если READY не придёт - сработает TimeoutStartSec= и юнит упадёт

Мини-шаблон:
```ini
[Service]
Type=notify
ExecStart=/usr/bin/myapp --notify
NotifyAccess=main
TimeoutStartSec=60s
```

[[Notify]]
[[Service types]]