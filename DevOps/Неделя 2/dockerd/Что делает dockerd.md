---
sr-due: 2026-04-21
sr-interval: 158
sr-ease: 230
---

#sr-due 

|Область|Что именно делает|
|---|---|
|📦 Образы|Pull / push / build, управление локальными образами|
|🔧 Контейнеры|create, start, stop, pause, restart, exec, attach и т.п.|
|🔁 Жизненный цикл|Рестарт политики (`--restart always`), контроль остановок|
|🖧 Сеть|Создание bridge, host, overlay сетей, NAT/iptables|
|🧱 Volume|Создание volume, монтирование, работа с volume-драйверами|
|📋 Build|Dockerfile → слои → образ (через BuildKit или старый builder)|
|🪵 Логирование|json-file, journald, syslog, fluentd, etc.|
|🔐 Безопасность|Seccomp, capabilities, AppArmor, selinux|
|📡 REST API|HTTP API (Docker Remote API) через `/var/run/docker.sock`|
|🧩 Плагины|Volume, network, authorization и т.п.|
|⚙️ Интеграция|systemd notify, метрики, events, cgroupd|
[[Что делает dockerd]]
[[dockerd]]