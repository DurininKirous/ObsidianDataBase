---
sr-due: 2025-10-22
sr-interval: 46
sr-ease: 230
---
#sr-due 
CI/CD - система сборки, тестирования, артефактирования и выката, состоящая из:
- Pipeline Engine - парсер и оркестратор пайплайнов (GitHub Actions, GitLab CI, Jenkins)
- Runners/Executors - рабочие узлы, выполнящие `job`
- Artifact & Cache Store - хранилища промежуточных и финальных результатов
- Secret Store - система управления секретами (встроенная или внешняя)
- Notification / Monitoring - алерты, статусы пайплайнов, отчёты
- Environment Provisioning - создние dev/stage/prod окружений
- Trigger system - правила, по которым запускается пайплайн
- Audit & Logs - отслеживание всего, что было выполнено

[[Архитектура CI CD пайплайна]]
[[Неделя 3]]