---
sr-due: 2025-08-06
sr-interval: 16
sr-ease: 250
---

#sr-due 
## 🚀 logrotate

### 📌 Что делает
- Управляет ротацией логов:
  - архивирует старые (`.1`, `.2.gz`),
  - удаляет слишком старые,
  - может перезапустить сервис после ротации.

---

### ⚙ Где конфиги
| Файл / Каталог           | Для чего                  |
|--------------------------|--------------------------|
| `/etc/logrotate.conf`    | Глобальный конфиг         |
| `/etc/logrotate.d/`      | Отдельные конфиги для сервисов |

---

### 🔥 Пример конфига
```conf
/var/log/nginx/*.log {
    daily
    rotate 14
    compress
    delaycompress
    missingok
    notifempty
    create 0640 www-data adm
    sharedscripts
    postrotate
        systemctl reload nginx > /dev/null 2>&1
    endscript
}
```
## 🚀 rsyslog

### 📌 Что делает

- Классический syslog-демон:
    
    - собирает логи ядра, crontab, ssh и прочих системных процессов,
        
    - пишет их в `/var/log/`.
        

---

### ⚙ Где конфиги

| Файл / Каталог          | Для чего               |
| ----------------------- | ---------------------- |
| `/etc/rsyslog.conf`     | Главный конфиг         |
| `/etc/rsyslog.d/*.conf` | Для отдельных сервисов |

[[logrotate, rsyslogd]]
[[Команды Linux]]