---
sr-due: 2025-09-24
sr-interval: 13
sr-ease: 210
---

#sr-due 
**Временные окружения, создаваемые на каждую ветку / MR**.

Пример:

review:
  stage: deploy
  script: ./deploy_review.sh $CI_COMMIT_REF_NAME
  environment:
    name: review/$CI_COMMIT_REF_NAME
    url: https://$CI_COMMIT_REF_NAME.review.example.com
    on_stop: stop_review
  rules:
    - if: '$CI_PIPELINE_SOURCE == "merge_request_event"'

Чтобы убрать:

stop_review:
  stage: cleanup
  script: ./destroy_review.sh $CI_COMMIT_REF_NAME
  environment:
    name: review/$CI_COMMIT_REF_NAME
    action: stop
  rules:
    - if: '$CI_PIPELINE_SOURCE == "merge_request_event"'
      when: manual

[[Review apps]]
[[DevOps Лагерь/Неделя 3/GitLab CI CD/Deployment/Deployment]]