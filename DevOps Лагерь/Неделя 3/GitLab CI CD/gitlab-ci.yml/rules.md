---
sr-due: 2025-10-12
sr-interval: 37
sr-ease: 230
---
#sr-due 
job:
  script: do-stuff
  rules:
    - if: '$CI_COMMIT_BRANCH == "main"'
    - if: '$CI_COMMIT_MESSAGE =~ /hotfix/'
Что делают rules:
определяют условия запуска job, используя:
- переменные среды GitLab CI ($CI_COMMIT_BRANCH, $CI_PIPELINE_SOURCE и т.п.)
- регулярные выражения
- логику приоритетов
- параметры: when:, allow_failure:, changes: 
Пример:
test-job:
  stage: test
  script:
    - echo "Running tests"
  rules:
    - if: '$CI_PIPELINE_SOURCE == "merge_request_event"'
      when: always
    - if: '$CI_COMMIT_BRANCH == "main"'
      when: always
    - when: never

[[rules]]
[[gitlab-ci.yml]]