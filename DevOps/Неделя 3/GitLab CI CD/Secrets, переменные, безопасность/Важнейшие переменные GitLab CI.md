---
sr-due: 2027-01-05
sr-interval: 310
sr-ease: 250
---

#sr-due

|Переменная|Что содержит|
|---|---|
|`CI_JOB_TOKEN`|токен job'а для доступа к API, Registry, Download|
|`CI_COMMIT_BRANCH`|имя текущей ветки|
|`CI_PIPELINE_SOURCE`|`push`, `web`, `trigger`, `schedule`, `merge_request_event`|
|`CI_PROJECT_DIR`|путь к директории проекта в runner'е|
|`CI_REGISTRY_IMAGE`|адрес Docker-репозитория GitLab|
[[Важнейшие переменные GitLab CI]]
[[Secrets, переменные, безопасность]]