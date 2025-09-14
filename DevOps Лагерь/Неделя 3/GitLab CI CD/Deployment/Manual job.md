---
sr-due: 2025-10-20
sr-interval: 41
sr-ease: 230
---

#sr-due 
deploy_prod:
  stage: deploy
  script: ./deploy_prod.sh
  environment:
    name: production
    url: https://example.com
  rules:
    - if: '$CI_COMMIT_BRANCH == "main"'
      when: manual
Деплой в `main` делается **только вручную**, через кнопку "Play" в UI.
[[Manual job]]
[[DevOps Лагерь/Неделя 3/GitLab CI CD/Deployment/Deployment]]