---
sr-due: 2025-10-31
sr-interval: 1
sr-ease: 230
---

#sr-due 
Назначение: логические срезы состояния системы и точки синхронизации. Не запускают процесс, лишь собирают юниты через зависимости.
Типовые:
- multi-user.target - серверный режим (сеть, сервисы, без GUI)
- graphical.target - как выше + графическая сессия
- rescue.target, emergency.target - аварийный режимы
Поля:
- \[Unit]: Wants=, Requires=, Before=, After= - кто входит
- \[Install]: Alias=, WantedBy= (на что переключаться по умолчанию)
Команды:
```bash
systemctl get-default
sudo systemctl set-default multi-user.target
sudo systemctl isolate rescue.target
systemctl list-dependencies multi-user.target
```
[[target]]
[[Units]]