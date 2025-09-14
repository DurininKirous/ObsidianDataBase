---
sr-due: 2025-09-23
sr-interval: 12
sr-ease: 210
---

#sr-due 
Это логическая сущность, которая описывает окружение, куда job что-то деплоит.
- Например: `staging`, `production`, `review/feature-x`.
- GitLab **отображает environments в UI**, позволяет:
    - отслеживать, что и куда задеплоено;
    - управлять автозавершением (auto_stop);
    - откатываться (`rollback to ...`);
    - использовать review apps (динамические среды).
пример:
deploy_staging:
  stage: deploy
  script: ./deploy.sh staging
  environment:
    name: staging
    url: https://staging.example.com

[[environment]]
[[DevOps Лагерь/Неделя 3/GitLab CI CD/Deployment/Deployment]]