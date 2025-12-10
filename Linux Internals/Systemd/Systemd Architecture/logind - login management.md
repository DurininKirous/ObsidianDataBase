---
sr-due: 2025-12-28
sr-interval: 34
sr-ease: 230
---

#sr-due 
- Роль: управление сессиями пользователей, сидениями, привязкой устройств, user slices/cgroups, linger (юзер-сервисы без активного логина), обработка кнопок питания/крышки
- Юнит: systemd-logind.service
- Инструменты: loginctl - смотреть/управлять сессиями: loginctl list-sessions, show-user, enable-linger user
- Интеграция: создаёт иерархии cgroup для пользователей -> лимиты/изоляция пользовательских процессов; взаимодействует с PID 1 при остановках/переключениях пользователей
[[logind - login management]]
[[systemd - PID 1 (main daemon)]]