---
sr-due: 2025-10-29
sr-interval: 51
sr-ease: 250
---

#sr-due 

| Практика                              | Зачем                                      |
| ------------------------------------- | ------------------------------------------ |
| `rules:` везде                        | `only/except` — устарело                   |
| `needs:` для ускорения                | DAG вместо линейных стадий                 |
| `parallel:` / `matrix:`               | тестирование и нагрузка                    |
| `rules: changes:`                     | запуск job’ов только при нужных изменениях |
| `when: manual`, `allow_failure`       | контроль релизов и экспериментов           |
| `artifacts:` + `dependencies:`        | бинарники, отчёты, деплой                  |
| `masked` и `protected` переменные     | защита secrets                             |
| `include:` + шаблоны                  | многофайловый пайплайн                     |
| `.gitlab-ci-local`, `glab`, `CI Lint` | локальная разработка и проверка            |
| `interruptible: true`, `auto_cancel:` | не тратить ресурсы на старые pipeline      |
[[Best practices checklist]]
[[DevOps Лагерь/Неделя 3/GitLab CI CD/Deployment/Deployment]]