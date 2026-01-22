---
sr-due: 2026-04-10
sr-interval: 92
sr-ease: 230
---

#sr-due 
Назначение: описывает монтирование файловой системы как unit. Именование: имя соответствует пути, - заменят /: /var/log -> var-log.mount
Ключевые поля (\[Mount]):
- What= (источник: устройство/UUID/NFS), Where= (точка монтирования), Type=, Options=
- Зависимости: можно ставить Before=local-fs.target/After= нужных устройств
Пример управления:
```bash
systemctl start var-log.mount
systemctl enable var-log.mount
systemctl status var-log.mount
```
[[Obsidian Vault/Rebrain/Studying/Linux Internals/Systemd/Units/mount]]
[[Units]]