---
sr-due: 2025-10-15
sr-interval: 39
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
[[DevOps Лагерь/Неделя 3/GitLab CI CD/Deployment/Deployment]]