---
sr-due: 2027-01-12
sr-interval: 315
sr-ease: 250
---

#sr-due 
workflow.rules - это правила, которые определяют: запускать весь пайплайн или нет.
Применяется до анализа stages и jobs. Если workflow.rules сказала when: never, pipeline не будет создан вообще.
workflow:
  rules:
    - if: '$CI_COMMIT_BRANCH == "main"'
      when: always
    - when: never
Отличие от `job.rules`:

| Механизм       | Управляет запуском         | Уровень                  |
| -------------- | -------------------------- | ------------------------ |
| workflow.rules | Запустить pipeline или нет | pipeline-wide (весь DAG) |
| rules (в job)  | Запускать job или нет      | job-level                |

Пример использования:

workflow:
  rules:
    - if: $CI_PIPELINE_SOURCE == "merge_request_event"
      when: always
    - if: $CI_COMMIT_BRANCH == "main"
      when: always
    - when: never
	
👉 Запускаем pipeline только:
- при пуше в `main`,
- или когда открыли Merge Request.
[[workflow]]
[[gitlab-ci.yml]]