---
sr-due: 2025-09-09
sr-interval: 43
sr-ease: 270
---

#sr-due 
*systemctl edit* - позволяет редактировать юнит/таймер без необходимости поиска файла и делает это безопасно
*systemctl revert* - откатывает все изменения через edit до изначального варианта, который идёт с пакетом
*systemctl cat* - выводит содержимое юнит файла сервиса
*systemctl list-units --type=service/socker* - вывод юнитов определенного типа
*systemctl list-timers* - то же самое для таймеров
*systemctl list-dependencies* - вывод зависимостей
*systemctl show* - показывает все свойства юнита
*systemctl kill* - отправить сигнал процессу юнита, можно конкретизировать сигнал, по умолчанию идёт сигнал SIGTERM (15)
[[Systemd]]
[[Systemctl (новое и полезное)]]