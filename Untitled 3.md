# 🚀 Summer DevOps Plan (3.5 месяца, июль — октябрь 2025)
🎯 Цель: к октябрю выйти на уверенный уровень Middle DevOps Engineer, с офферами от Яндекс / VK / Авито / Тинькофф

---

## 🗓 Недели (основные темы)
| Неделя | Основная тема                                                                            | Python/Go + Алгоритмы                                                       |
| ------ | ---------------------------------------------------------------------------------------- | --------------------------------------------------------------------------- |
| 1      | Linux + Сети                                                                             | Python: os, subprocess, pathlib, argparse, logging. Algo: массивы, строки   |
| 2      | Docker + docker-compose                                                                  | Go: basics, flag, os, CLI tools. Algo: dict/set, prefix sums                |
| 3      | CI/CD (GitHub Actions / GitLab CI) + Git                                                 | Python: requests, json, pytest. Algo: stack, queue                          |
| 4      | Kubernetes: Pods, Deployments, Services, ConfigMap, Secret                               | Go: HTTP client/server, context. Algo: linked list, binary search           |
| 5      | Kubernetes: Ingress, Probes, Limits + Helm                                               | Python: asyncio, многопоток. Algo: BFS, DFS                                 |
| 6      | Terraform + Ansible                                                                      | Go: goroutines, channels, concurrency. Algo: heap, сортировки               |
| 7      | Monitoring: Prometheus, Grafana + Loki/EFK                                               | Python: парсер nginx логов, psutil. Algo: binary tree, BST                  |
| 8      | Базы данных: PostgreSQL, MySQL, Redis (docker-compose, replication, monitoring, backups) | Go: SSH healthcheck, DB conn. Algo: sliding window                          |
| 9      | Kafka + очереди                                                                          | Python: consumer для Kafka. Algo: графы, shortest path                      |
| 10     | HA, CAP, отказоустойчивость + Kafka Streams                                              | Go: GRPC, graceful shutdown. Algo: backtracking, combinatorics              |
| 11     | Безопасность (SSL/TLS, RBAC, Linux Hardening)                                            | Python: SSL cert check, security скрипты. Algo: повторение всего            |
| 12     | Архитектуры микросервисов, балансировщики, circuit breakers                              | Go: REST+GRPC мультисервис. Algo: сложные mix задачи                        |
| 13     | Финализация, mock-собесы, фиксы слабых мест                                              | Python+Go: docker-compose stack, end2end tests. Algo: стабильное повторение |

---
Проекты по ЯП'ам:

✅ **Неделя 3:**

- **Python:** healthcheck со списком сайтов, логами и async.
    
- **Go:** CLI утилита для поиска больших файлов (аналог `ncdu` lite).

✅ **Неделя 6:**

- **Python:** FastAPI REST сервис с `/status`, `/metrics`.
    
- **Go:** HTTP сервер, который проверяет список сайтов параллельно и отдаёт JSON результат.

✅ **Неделя 9:**

- **Python:** лог-анализатор nginx log + алерты в Telegram.
    
- **Go:** SSH checker, который пингует список серверов и даёт summary.

✅ **Неделя 12-13:**

- **Python + Go вместе:**
    
    - Python service: healthcheck + логгер в PostgreSQL
        
    - Go service: REST API который отдаёт health статус из БД.
        
- Всё в `docker-compose`, покрыто тестами, с `Makefile` для запуска.
---
## ⏰ Ежедневный график (8 часов учёбы)
> ✍ Основное правило — **8 часов учёбы и никакой вины за отдых остальное время.**

| Время             | Что делать                                                                |
| ----------------- | ------------------------------------------------------------------------- |
| **7:00 — 8:30**   | 🏃 Пробежка / зарядка ➔ душ ➔ завтрак                                     |
| **8:30 — 10:30**  | 🛠 Основная DevOps тема недели (Linux / Docker / k8s / Terraform / Kafka) |
| **10:30 — 10:45** | ☕ Перерыв                                                                 |
| **10:45 — 12:15** | 🛠 Продолжение практики (деплой, ingress, terraform apply)                |
| **12:15 — 13:00** | 🍽 Лёгкий обед / отдых                                                    |
| **13:00 — 14:30** | 🐍 Python / 🐹 Go + алгоритмы (~1.5 ч, можно чередовать или 45+45)        |
| **14:30 — 15:00** | ☕ Перерыв / прогулка                                                      |
| **15:00 — 16:30** | 🛠 CI/CD, monitoring, kafka consumers, helm                               |
| **16:30 — 16:45** | ☕ Перерыв                                                                 |
| **16:45 — 18:15** | 📚 Документация, best practices, конспекты, самопрослушивание             |
| **18:15 ➔**       | 🏋 Силовая тренировка (3 р/нед вечером) или просто отдых                  |
| **20:00 — 21:00** | Ужин + социализация / кино / книги                                        |
| **21:00 — 22:00** | Спокойный отход ко сну                                                    |
| **22:00**         | 😴 Сон                                                                    |

---

## 🏋 Силовые тренировки
- **3 раза в неделю вечером (например Пн, Ср, Пт)** — полноценная тренировка (зал или дома).
- В остальные дни — только утренняя пробежка / зарядка.

---

## 📝 Воскресенье
- **~1-1.5 часа mock-собес по всей теме недели** + немного Linux/сети/алгоритмов.
- Остальное — полный отдых и жизнь 🌞

---

# ✅ Твой чеклист прогресса
- [x] 📚 Linux + Сети освоены
- [x] 🐳 Docker + docker-compose написаны для pet проектов
- [ ] ⚙ CI/CD пайплайны (GitHub Actions / GitLab CI) работают
- [ ] ☸ Kubernetes: Pods, Deployments, Ingress, Helm в продакшн уровне
- [ ] 📦 Terraform + Ansible для IaC
- [ ] 📊 Monitoring stack (Prometheus + Grafana + Loki)
- [ ] 🗄 PostgreSQL / MySQL / Redis: docker-compose, replication, monitoring, backups
- [ ] 🚀 Kafka: producer / consumer на Python/Go
- [ ] 🔐 SSL/TLS, RBAC, fail2ban, hardening Linux
- [ ] 🧩 Архитектуры микросервисов + балансировщики
- [ ] 📝 Python / Go скрипты для healthchecks, kafka, API
- [ ] 💻 Решено >100 задач на leetcode/codeforces
- [ ] 🎤 Mock собесы каждое воскресенье
- [ ] 🚀 Готовое резюме и GitHub с README + архитектурами

---

# ❤️ Летнее напоминание
> 🌞 Это лето — единственное лето 2025 года.  
> Не забывай наслаждаться солнцем, гулять, кататься, проводить время с друзьями.  
> **Middle DevOps будет, но кайф от жизни тоже важен.**
	