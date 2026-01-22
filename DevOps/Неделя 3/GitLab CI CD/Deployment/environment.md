---
sr-due: 2026-06-02
sr-interval: 145
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
[[Obsidian Vault/Rebrain/Studying/DevOps/Неделя 3/GitLab CI CD/Deployment/Deployment]]