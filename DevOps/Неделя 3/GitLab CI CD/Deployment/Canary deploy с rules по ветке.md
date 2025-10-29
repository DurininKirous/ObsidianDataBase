---
sr-due: 2026-01-15
sr-interval: 92
sr-ease: 230
---

#sr-due 
canary:
  stage: deploy
  script: ./deploy_canary.sh
  environment:
    name: canary
  rules:
    - if: '$CI_COMMIT_REF_NAME =~ /^release-/'

[[Canary deploy с rules по ветке]]
[[Obsidian Vault/Rebrain/Studying/DevOps/Неделя 3/GitLab CI CD/Deployment/Deployment]]