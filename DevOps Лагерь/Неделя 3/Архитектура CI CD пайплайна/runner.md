---
sr-due: 2025-10-10
sr-interval: 32
sr-ease: 210
---

#sr-due 
> Runner - агент, который тянет job и исполняет её

| Характеристика | GitHub Actions                   | GitLab CI                         |
| -------------- | -------------------------------- | --------------------------------- |
| Варианты       | Ubuntu / macOS / Windows         | Docker, shell, Kubernetes runner  |
| Изоляция       | Каждый job → отдельный контейнер | Runner запускает docker контейнер |
| Кастомизация   | Только self-hosted               | Любой executor                    |
| Кэш            | actions/cache                    | встроенный                        |
### Важное:
- Runner может быть **self-hosted** → контроль, кэш, docker, SSH, VPN
- **GitHub runner** запускает каждый job в **fresh instance**
- GitLab позволяет использовать **один и тот же runner** на k8s / shell


[[runner]]
[[Архитектура CI CD пайплайна]]